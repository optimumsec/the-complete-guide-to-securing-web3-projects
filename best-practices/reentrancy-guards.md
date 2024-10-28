### Use Reentrancy Guards

Reentrancy is generally not expected behavior in most smart contracts, with the exception of callback systems like those used in Uniswap. As a best practice, this behavior should be restricted unless explicitly necessary.

In practice, all state-changing functions that include external calls should be protected by a reentrancy guard by default, and any removal of this protection should only occur after a thorough assessment of its impact.

If gas optimization is a concern, consider using a reentrancy guard library that leverages [transient storage](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/ReentrancyGuardTransient.sol). Be aware that some EVM chains do not support transient storage. For details on opcode support across different chains, refer to [evmdiff.com](https://www.evmdiff.com/features?feature=opcodes).
