# 🔐 Smart Contract Security Best Practices Guide

When web3 users are asked what influences their preference for one decentralized application (dApp) over another, **security** often emerges as a primary concern. Users seek platforms that have never been hacked and demonstrate a serious commitment to security. 

While there is extensive literature on smart contract vulnerabilities, discussions surrounding best practices and preventative measures are frequently underrepresented. Security extends beyond merely identifying flaws; it involves proactively integrating protective measures at every stage of the smart contract development process. 

This guide aims to serve as a comprehensive resource for best practices across the software development lifecycle: Design, Coding, Testing, Pre-Deployment, Deployment, Ongoing Upgrades, and Ongoing Operations. If you are starting a new project or looking to strengthen the security practices of your current one, this guide can act as a one-stop shop, helping you navigate the complexities of secure development and deployment. By covering every phase of the lifecycle, it provides actionable insights and frameworks to minimize vulnerabilities, streamline workflows, and establish a culture of security from inception to operation.


## 🛡️ Design
[Design a Gradual Path Towards Immutability](./best-practices/gradual-immutability-path.md)

[Conduct an Actor-Based Threat Modeling](./best-practices/actor-based-threat-modeling.md)

[Establish a Role-Based Access Control (RBAC) Model](./best-practices/rbac.md)

[Funds Isolation By Design](./best-practices/funds-isolation-by-design.md)

[Circuit Breakers](./best-practices/circuit-breakers.md)


## 🛡️ Coding
[Use a Spell Checker](./best-practices/use-spell-checker.md)

[Use an Up To Date Compiler Version](./best-practices/use-up-to-date-compiler-version.md)

[Security Driven Development](./best-practices/security-driven-development.md)

[Prefer Unstructured Storage For Upgradeable Contracts](./best-practices/unstructured-storage.md)

[Avoid Vendoring Dependencies](./best-practices/avoid-vendoring.md)

[Use a Plugin For Safe Upgrades](./best-practices/plugin-for-safe-upgrades.md)

[Use Reentrancy Guards](./best-practices/reentrancy-guards.md)

[Revert/Return Early](./best-practices/revert-return-early.md)

[Avoid Unlimited ERC-20 Approvals](./best-practices/avoid-unlimited-erc20-approvals.md)

[Use the Safe ERC-20 Library](./best-practices/safe-erc20-library.md)

[Use the SafeCast Library](./best-practices/safe-cast-library.md)

[Use Cryptographic Libraries](./best-practices/use-cryptographic-libs.md)

[Prefer to Avoid Low Level Calls](./best-practices/avoid-low-level-calls.md)

[Careful Vetting of Unchecked Blocks](./best-practices/careful-vetting-of-unchecked-blocks.md)

[Avoid Arbitrary Low Level External Calls](./best-practices/avoid-arbitrary-external-calls.md)

[Follow the EIP-712 Standard for Digital Signatures](./best-practices/adhere-to-eip-712.md)

[Vetting Process for External Tokens](./best-practices/vetting-process-for-external-tokens.md)

## 🛡️ Testing
[Develop Comprehensive Unit Tests](./best-practices/unit-tests.md)

[Develop Comprehensive Integration Tests](./best-practices/integration-tests.md)

[Develop Comprehensive Fuzzing Tests](./best-practices/fuzzing-tests.md)

[Develop Comprehensive Fork Tests](./best-practices/fork-tests.md)

[Track and Optimize Test Coverage](./best-practices/optimize-test-coverage.md)

[Conduct End to End Testing on Testnet](./best-practices/e2e-tests.md)

## 🛡️ Pre Deployment
[Internal Security Reviews](./best-practices/internal-security-reviews.md)

[The Importance of Code Freeze Before an External Security Review](./best-practices/importance-of-code-freeze-before-an-external-review.md)

[External Security Reviews](./best-practices/external-security-reviews.md)

[Implement Robust Monitoring Security Rules](./best-practices/monitoring-security-rules.md)

[Leverage Security Reviews to Define Monitoring Security Rules](./best-practices/tailor-made-security-rules.md)

[The Importance of Code Freeze Before Deployment](./best-practices/importance-of-code-freeze-before-deployment.md)

[Establish a Contingency Plan](./best-practices/establish-contingency-plan.md)

## 🛡️ Deployment

[Adopt a Safe Launch Strategy](./best-practices/soft-launch.md)

[Never Deploy Code That Was Not Reviewed Externally](./best-practices/never-deploy-without-review.md)

[Launch a Bug Bounty Program](./best-practices/bug-bounty.md)

## 🛡️ On-going Upgrades
[WIP] [Backwards Compatibility and State Fixes]() (state, function sigs)
[WIP] [Differential Tests]()
[WIP] [Unit tests as regression tests]

## 🛡️ On-going Operations
[Establish a Chief Of Security Role](./best-practices/chief-of-security.md)

[Establish a Security Council](./best-practices/security-council.md)