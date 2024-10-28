# Smart Contracts Security Best Practices
While much has been written about smart contract vulnerabilities, discussions around best practices and preventative measures are often lacking. Security is not just about identifying flaws but about proactively embedding protection throughout every stage of the smart contract development process. started a new project? make sure to read this list that documents what you should do from the beginning til launch.
The following list provides a set of best practices focused on minimizing risks before they arise, ensuring that security is built into the code from the ground up.

## Design & Coding
[Use Spelling Checkers](./best-practices/use-spelling-checkers.md)

[Use Up To Date Compiler Versions](./best-practices/use-up-to-date-compiler-versions.md)

[Design A Gradual Path Towards Decentralization]() well known battle tested components like tokens can be immutable, tradeoff between the maturity of the code and the trust assumptions.

[Prefer Unstructured Storage For Upgradeable Contracts](./best-practices/unstructured-storage.md)

[Use A Plugin For Safe Upgrades](./best-practices/plugin-for-safe-upgrades.md)

[Funds Isolation By Design](./best-practices/funds-isolation-by-design.md)

[Use Reentrancy Guards](./best-practices/reentrancy-guards.md)

[Revert/Return Early](./best-practices/revert-return-early.md)

[Avoid Unlimited ERC-20 Approvals](./best-practices/avoid-unlimited-erc20-approvals.md)

[Use The Safe ERC-20 Library](./best-practices/safe-erc20-library.md)

[Use The SafeCast Library](./best-practices/safe-cast-library.md)

[Prefer To Avoid Low Level Calls](./best-practices/avoid-low-level-calls.md)

[Careful Vetting Of Unchecked Blocks](./best-practices/careful-vetting-of-unchecked-blocks.md)

[Avoid Arbitrary External Calls](./best-practices/avoid-arbitrary-external-calls.md)

[Adhere to EIP-712](./best-practices/use-up-to-date-compiler-versions.md)

[Internal Vetting Process For External Tokens](./best-practices/use-spelling-checkers.md)

[Internal Security Reviews](./best-practices/internal-security-reviews.md)

[External Security Reviews](./best-practices/external-security-reviews.md) - fixes should be reviewed by the auditor. three way handshake. More than a single review. Pick the right team. allocate time to find the right ones and also allocate time for fixes.

## Testing
[Run A Testnet Campaign]()

[Run An Incentivized Testnet Campaign]()

[The Importance Of Code Freeze]()

## Deployment
[Soft Launch]()

[Never Deploy Code That Was Not Reviewed Externally]()

[Bug Bounty]()

## On-going Upgrades