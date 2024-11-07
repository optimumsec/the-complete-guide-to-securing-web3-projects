# Smart Contract Security Best Practices

When web3 users are asked what influences their preference for one decentralized application (dApp) over another, security often emerges as a primary concern. Users seek platforms that have never been hacked and demonstrate a serious commitment to security. 

While there is extensive literature on smart contract vulnerabilities, discussions surrounding best practices and preventative measures are frequently underrepresented. Security extends beyond merely identifying flaws; it involves proactively integrating protective measures at every stage of the smart contract development process. 

This document aims to serve as a comprehensive resource for best practices across the software development lifecycle: Design & Coding, Testing, Deployment, Ongoing Upgrades, and Ongoing Operations. 

The following list outlines key practices focused on minimizing risks before they occur, ensuring that security is ingrained in the code from the outset.

## Design
[Design A Gradual Path Towards Decentralization](./best-practices/gradual-immutability-path.md)

[Actor-Based Threat Modeling](./best-practices/actor-based-threat-modeling.md)

[Establish a Role-Based Access Control (RBAC) Model](./best-practices/rbac.md)

[Funds Isolation By Design](./best-practices/funds-isolation-by-design.md)

[Circuit Breakers](./best-practices/circuit-breakers.md)


## Coding
[Use A Spell Checker](./best-practices/use-spell-checker.md)

[Use An Up To Date Compiler Version](./best-practices/use-up-to-date-compiler-version.md)

[Security Driven Development](./best-practices/security-driven-development.md)

[Prefer Unstructured Storage For Upgradeable Contracts](./best-practices/unstructured-storage.md)

[Use A Plugin For Safe Upgrades](./best-practices/plugin-for-safe-upgrades.md)

[Use Reentrancy Guards](./best-practices/reentrancy-guards.md)

[Revert/Return Early](./best-practices/revert-return-early.md)

[Avoid Unlimited ERC-20 Approvals](./best-practices/avoid-unlimited-erc20-approvals.md)

[Use The Safe ERC-20 Library](./best-practices/safe-erc20-library.md)

[Use The SafeCast Library](./best-practices/safe-cast-library.md)

[TBD] Use Math Libraries

[Use Cryptographic Libraries](./best-practices/use-cryptographic-libs.md)

[Prefer To Avoid Low Level Calls](./best-practices/avoid-low-level-calls.md)

[Careful Vetting Of Unchecked Blocks](./best-practices/careful-vetting-of-unchecked-blocks.md)

[Avoid Arbitrary External Calls](./best-practices/avoid-arbitrary-external-calls.md)

[Adhere to EIP-712](./best-practices/use-up-to-date-compiler-versions.md)

[Internal Vetting Process For External Tokens](./best-practices/use-spelling-checkers.md)

## Testing
[Unit Testing]()

[Integration Testing]()

[Fuzz Testing]()

[Simulation Testing]()

[Testnet Campaign]()

[Run An Incentivized Testnet Campaign]()

[The Importance Of Code Freeze]()


## Deployment
[Contingency Plan]()

[Soft Launch]()

[Never Deploy Code That Was Not Reviewed Externally](./best-practices/never-deploy-without-review.md)

[Bug Bounty]()

[On-chain Deployment Script]()

## On-going Upgrades
[Fork Testing]()

## On-going Operations
[Establish A Chief Of Security Role](./best-practices/chief-of-security.md)

[Establish A Security Council](./best-practices/security-council.md)

[Internal Security Reviews](./best-practices/internal-security-reviews.md)

[External Security Reviews](./best-practices/external-security-reviews.md)
