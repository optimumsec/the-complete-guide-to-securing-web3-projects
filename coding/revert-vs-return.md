## Revert vs Return

### TL;DR Rules

**Revert** when any of the following is true:

- The function is **state-changing** and a precondition, invariant, or authorization check fails.
- A **security boundary** would be crossed (e.g., missing role, paused state, supply cap breach).
- A downstream call’s failure would produce **partial state** or **ambiguous outcome**.
- The caller **cannot safely proceed** without this operation succeeding.

**Return** when all of the following are true:

- The function is **non–state-changing** (`view`/`pure`) *or* the failure is an **expected, non-security** outcome.
- The caller can **safely decide next steps** using the returned value.
- Soft-failure improves **UX or composability** without hiding risk (e.g., a probe, simulation, or off-chain read).

> Default to **revert** for write functions; opt into **return** for read/probe helpers.

### Decision Tree

1. **Will state change on success?**
   - **Yes** → If any precondition fails → **Revert**.
   - **No** → Proceed.
2. **Is the check about permissions, invariants, or monetary safety?**
   - **Yes** → **Revert**.
   - **No** → Proceed.
3. **Can the caller safely handle a soft-fail?** (No ambiguity, no partial effects)
   - **No** → **Revert**.
   - **Yes** → **Return** a boolean/enum/optional.


### When to **Revert**

- **Authorization & Pausing**: `onlyOwner`, role checks, `Pausable` state.
- **Input Validation**: malformed parameters, invalid array lengths, zero address (when unsafe), overflow conditions not handled by compiler.
- **Economic/Safety Invariants**: caps exceeded, debt ratios violated, collateralization too low, auction not active, deadlines expired.
- **Atomicity & Funds Movement**: any transfer/mint/burn that must succeed to avoid inconsistent state or loss of funds.
- **Protocol-Level Guarantees**: conditions documented as MUST in your spec/README.
- **Unsupported Tokens/Behaviors** when interacting with external standards.

> Use **custom errors** (e.g., `error NotAuthorized();`) for low gas and clearer decoding.


### When to **Return** (Soft-Fail / Informational)

- **Probing/Quoting**: returning whether an action *would* succeed and at what price (`view` quote functions).
- **Best-Effort Operations** that are explicitly non-critical and have **no side effects** on failure.
- **Eligibility Checks** that frontends can call off-chain to pre-screen (e.g., `canClaim(address) returns (bool)`), leaving the write path to **revert** if wrong.
- **Batch Reads** where some elements might be missing; return per-item statuses instead of failing the entire batch.
- **Upgradeable feature flags** or **optional modules** where absence is not a security boundary.

> For write paths, prefer reverting on any failed per-item operation unless the **spec** promises partial success and you **return a per-item report**.


### Mixed Pattern: Soft-Check Helper + Hard-Fail Writer

- Provide a \`\`\*\* helper\*\* that returns `(bool ok, bytes reason)` or an enum.
- The **state-changing** function calls the same internal logic and **reverts** on failure.

```solidity
error NotWhitelisted();

function canMint(address user, uint256 amount) public view returns (bool ok, bytes32 reason) {
    if (!whitelist[user]) return (false, bytes32("NOT_WHITELISTED"));
    if (totalSupply + amount > cap) return (false, bytes32("CAP_EXCEEDED"));
    return (true, bytes32(0));
}

function mint(address to, uint256 amount) external {
    (bool ok, bytes32 reason) = canMint(to, amount);
    if (!ok) revert(reason == bytes32("NOT_WHITELISTED") ? NotWhitelisted() : CapExceeded());
    _mint(to, amount);
}
```

This keeps UX friendly for off-chain callers while keeping on-chain safety strict.


### External Calls: `try/catch` vs Bubble

- If the callee’s failure should **abort your operation**, let the revert **bubble** or explicitly **revert**.
- Use `try/catch` to **translate** low-level failures into your own **custom errors** or **soft-return** for *read* probes.

```solidity
try priceOracle.getPrice(token) returns (uint256 p) {
    return p;
} catch {
    // For reads: return a sentinel, let frontend decide.
    return 0; // document clearly!
}
```

For **writes**, prefer reverting if the external dependency fails and your state would be ambiguous otherwise.


### ERC-20 Transfers: Revert by Default

- Different tokens either **revert** or **return false** on failure. Use OZ’s `SafeERC20` to **normalize** to reverts for safety.
- Avoid ignoring return values from `transfer`/`transferFrom`.

```solidity
using SafeERC20 for IERC20;

token.safeTransfer(to, amount); // reverts on failure across well-known noncompliant tokens
```

If you design your own token-like interface, **document** whether failures revert or return, and remain consistent.


### View/Pure Functions

- Never revert for **normal absence** of data (e.g., querying non-existent optional record); return `false`, `0`, or empty structs.
- Do revert on **caller misuse** even in views (e.g., invalid index) if it prevents misinterpretation.


### Gas, UX & Composability Considerations

- **Reverts** abort execution and undo state changes; callers must handle failure paths.
- **Soft-returns** enable **simulation and batching** but require **strict caller checks**.
- For **batch writes**, consider:
  - `all-or-nothing` (revert entire batch on first failure), or
  - `best-effort` with detailed per-item results and **events** describing partial success.

Document the choice in your spec and tests.


### Security Pitfalls & Anti-Patterns

- **Silent Fail-Open**: returning `true` on error, or returning nothing and proceeding.
- **Ignoring Return Values**: especially for ERC-20-like calls.
- **Access Control Soft-Fail**: returning `false` instead of reverting on unauthorized write.
- **Ambiguous Outcomes**: state changed while reporting failure.
- **Front-Running Windows from Soft-Fail**: if soft-fail reveals intent, ensure no exploitable timing leak.
- **Hidden Assumptions**: view helpers that say `true` but the write path can still revert due to race conditions; mitigate with **checks-effects-interactions** and **fresh reads**.