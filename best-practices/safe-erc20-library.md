### Use The Safe ERC-20 Library

When working with third-party ERC20 tokens, using the [SafeERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/utils/SafeERC20.sol) library is crucial to avoid common pitfalls. Functions like `safeTransfer` and `safeApprove` include additional safety checks that standard ERC20 functions often lack. 

For example, SafeERC20 ensures that the target address is a contract, not an externally owned account (EOA), preventing unintended interactions with non-contract addresses. It also addresses issues with non-standard tokens that may return false instead of reverting on failure.