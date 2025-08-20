## Core--Periphery Design Pattern for Immutable Protocols

For teams that decide **not** to use upgradeable contracts (see the
[gradual immutability
path](https://github.com/optimumsec/the-complete-guide-to-securing-web3-protocols/blob/main/design/gradual-immutability-path.md)),
the **core--periphery split** is a practical design choice that can
minimize security issues while still allowing controlled changes of functionality.


### What Is the Core--Periphery Split?

The **core** is the immutable, minimal set of contracts that define
protocol-critical logic and invariants.
The **periphery** is the replaceable layer that handles user
interactions, UX improvements, and convenience features.

#### Core

-   Immutable once deployed.
-   Holds critical state and enforces protocol-level invariants.
-   Example: Uniswap V2/V3 Pool contracts (AMM math, reserves, invariant
    checks).

#### Periphery

-   Can be re-deployed and versioned over time.
-   Abstracts away complexity and adds features like batching,
    multicall, safer UX.
-   Example: Uniswap Router, NonfungiblePositionManager.


### Why Use This Pattern?

-   **Security:** Core stays locked down, surface area minimized.
-   **Flexibility:** Teams can adapt UX, improve efficiency, or patch
    integration bugs without touching core.
-   **Clarity:** Easier to communicate security guarantees: "The pool
    logic is immutable. Routers can change."


### Upgrade Strategy Without Proxies

Even if core is immutable, periphery contracts can evolve. Typical
approaches include:

-   **Versioned Routers:** Deploy new routers with improved logic; users
    migrate voluntarily.
-   **Registries:** Maintain a registry contract pointing to the latest
    periphery; frontends can read from it.
-   **Migrations:** Encourage/force users to migrate state from old
    periphery to new periphery.


### Security Model

-   **Core**: must be fully audited, formally verified if possible, and
    designed for immutability.
-   **Periphery**: can be updated, but still requires review since it
    can influence user behavior.
-   **Interaction**: Core contracts should never trust periphery; only
    enforce strict invariants.


### Common Patterns

-   **Router → Pool Calls:** Router bundles user actions and calls into
    pools.
-   **Callback Interfaces:** Core pools define strict callback
    requirements, which routers must satisfy.
-   **Position Managers:** Higher-level contracts for abstracting LP
    positions.
-   **Fee Hooks / Incentives:** Kept in periphery to avoid contaminating
    invariant logic.


### Pitfalls

-   **Too Much in Periphery:** If periphery enforces invariants instead
    of core, security assumptions break.
-   **Silent Upgrades:** Replacing periphery without notice can create
    governance or trust issues.
-   **Registry Risks:** If the registry is compromised, users may be
    routed to malicious periphery contracts.

### Example: Minimal Core/Periphery Split

``` solidity
// Core: immutable pool
contract Pool {
    uint112 reserve0;
    uint112 reserve1;

    function swap(uint amount0Out, uint amount1Out) external {
        // Invariant: x * y >= k
        require(amount0Out == 0 || amount1Out == 0, "Only one side out");
        // ...
    }
}

// Periphery: router that interacts with core
contract Router {
    function swapExactTokensForTokens(...) external {
        // Handle approvals, slippage checks, path routing
        Pool(pool).swap(...);
    }
}
```