## Beware of "NFT Front Running" in ERC-721 Tokenization

When designing ERC-721 tokens that represent positions, claims, or other dynamic on-chain assets, a subtle but critical vulnerability may arise: **NFT front running**.

This occurs when the seller of a tradeable NFT can degrade the value of the token right before selling—leaving the buyer with a useless or significantly devalued asset.


### The Problem

Many NFTs do not just hold metadata; they also map to *storage inside a smart contract* that represents valuable state (e.g., liquidity, collateral, staking shares).

The ERC-721 `tokenId` is used to access that storage. However, **the** `tokenId` itself does not change when the storage state changes. This allows a malicious seller to:

1. List or offer their NFT for sale (e.g., on OpenSea, Blur, or a custom marketplace).
2. Before the trade executes, insert an on-chain transaction that **depreciates the underlying value** of the token—such as withdrawing liquidity or redeeming collateral.
3. The buyer still receives the `tokenId`, but it now points to depleted or useless storage.

The buyer has no way to guarantee that the `tokenId` still represents the same value as when the order was signed.


### Concrete Example: Uniswap V3 Positions

Uniswap V3 liquidity positions are represented as ERC-721 tokens.

- Suppose Alice owns a Uniswap V3 position NFT with $10,000 of liquidity.
- She lists it for sale on an NFT marketplace.
- Bob agrees to buy it, thinking it includes $10,000 worth of liquidity.
- Right before the trade settles, Alice front runs Bob’s purchase by calling `decreaseLiquidity` and `collect`.
- Now the NFT is still valid, but represents an empty position.
- Bob has purchased a worthless token.

This risk exists in **any NFT design where** the `tokenId` is tied to mutable storage and the buyer cannot enforce that storage is unchanged between signing and settlement.


### Other Vulnerable Designs

- **Staking share NFTs**: If the NFT represents a user’s stake, the seller can unstake right before selling.
- **Vault share NFTs**: If the NFT maps to claimable assets, the seller can withdraw them first.
- **Derivative position NFTs**: If the NFT represents leveraged or collateralized positions, the seller can close/withdraw parts before the transfer.


### Proposed Solution

The root cause is that **a single** `tokenId` is expected to both identify the NFT and the storage data it represents.

To prevent front running, we propose **decoupling the identity of the NFT from its storage state.**

#### Two Identifiers

- **Internal Identifier**

  - Constant throughout the life cycle of the position.
  - Implemented as a counter (`internal_id`).
  - Used to reference the actual storage (liquidity, collateral, staking balance, etc.).

- **External Identifier**

  - Represents a *specific snapshot of the internal identifier’s state*.
  - Used as the `tokenId` in the ERC-721 interface.
  - Generated as:

  ```
  external_id = hash(internal_id, version)
  ```

  where `version` increments every time the storage state changes.

#### Lifecycle

1. **Creation**

   - When a new position is created, assign it a fresh `internal_id`.
   - Mint an NFT with `external_id = hash(internal_id, 0)`.

2. **State Change**

   - Burn the existing external NFT.
   - Increment the version counter for that `internal_id`.
   - Mint a new NFT with `external_id = hash(internal_id, version)`.

3. **Transfer**

   - Buyers always know that the NFT they receive maps to a specific version of storage.
   - If a seller changes the storage before selling, a *new tokenId must be minted*—invalidating any old listings or signatures.


### Benefits

- Prevents sellers from front running by ensuring **state changes always produce a new NFT**.
- Makes NFT trades safer, especially for financialized NFTs (positions, shares, derivatives).
- Provides a clear, auditable history of changes (via incremented versions).


### Summary

If your ERC-721 tokens reference mutable on-chain state, beware of **NFT front running**.

By introducing a separation between internal (constant) and external (versioned) identifiers, and forcing state changes to mint new NFTs, you eliminate the possibility for sellers to front run buyers by draining or altering the token’s underlying value.

This design pattern ensures that NFTs remain **trustworthy representations of on-chain assets**, protecting both protocols and their users.