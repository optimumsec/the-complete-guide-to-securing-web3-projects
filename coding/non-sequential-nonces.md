## Consider Non-Sequential Nonces for Digital Signatures

### Introduction

When building smart contracts or blockchain-based applications that rely on off-chain signed messages, managing nonces properly is important. Nonces prevent replay attacks, but the way they are chosen can also affect **flexibility and usability** of your dApp.  

> This recommendation is **mainly relevant when sequential nonces are not intended functionality**. If your application does not require strict ordering of signed messages, non-sequential nonces allow more flexibility without enforcing artificial execution order.

Nonces are **per user** — each user has their own set of nonces. Two different users can use the same nonce value without conflict, because replay protection is scoped to the signer.


### Sequential vs Non-Sequential Nonces

#### Sequential Nonces

Sequential nonces increment by 1 for each message:

```text
nonce = 0, 1, 2, 3, ...
```

**Pros:**

- Simple to implement
- Easy to track

**Cons:**

- **Enforces strict order of execution.** Messages must be submitted in the exact sequence, otherwise they fail.
- Can limit dApp usability when multiple signed messages need to be executed in parallel or out-of-order.
- Adds unnecessary complexity for users or integrations that want flexibility.

#### Non-Sequential Nonces

Non-sequential nonces are **randomized or unique identifiers** that do not follow a predictable order:

```text
nonce = 0x92f3a1, 0x7b4d8c, 0x4a1f3b, ...
```

**Pros:**

- No enforced execution order — messages can be executed in any order.
- Supports parallel execution of multiple signed messages.
- Reduces friction for dApps where order is not important.
- Still prevents replay attacks, as each nonce is unique per user.

**Cons / Considerations:**

- Requires storing all used nonces for verification, which is slightly **more gas heavy** than a single sequential counter per user.
- **Avoiding collisions:** Off-chain nonce generation must check against all previously used nonces for that user. This can be done by:
  1. Querying the contract for all used nonces for the user (or a mapping of recent nonces if optimized).  
  2. Generating a sufficiently large random or pseudo-random nonce to minimize the probability of collision.  
  3. Optionally, retrying nonce generation if a collision is detected.


### Recommended On-Chain Verification Pattern

1. **Store used nonces per user**

```solidity
mapping(address => mapping(bytes32 => bool)) public usedNonces;
```

2. **Verify nonce validity before executing the transaction**

```solidity
function executeSignedAction(
    address signer,
    bytes32 nonce,
    bytes calldata signature
) external {
    require(!usedNonces[signer][nonce], "Nonce already used");

    bytes32 messageHash = keccak256(abi.encodePacked(msg.sender, nonce));
    require(recoverSigner(messageHash, signature) == signer, "Invalid signature");

    usedNonces[signer][nonce] = true;

    // Execute action
}
```

3. **Recover signer from signature**

```solidity
function recoverSigner(bytes32 hash, bytes memory signature) internal pure returns (address) {
    bytes32 ethSignedHash = ECDSA.toEthSignedMessageHash(hash);
    return ECDSA.recover(ethSignedHash, signature);
}
```