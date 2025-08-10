# 🔐 The Complete Guide to Securing Web3 Protocols

Security is a top priority for web3 users when choosing decentralized applications (dApps). They prefer platforms with a proven track record of safety and a clear commitment to secure practices. While much has been written about vulnerabilities in smart contracts, there’s less focus on practical steps to prevent them.

This guide offers a clear, actionable framework for integrating security throughout the smart contract lifecycle—from design and coding to deployment and ongoing maintenance. Whether launching a new project or improving an existing one, use this resource to reduce risks, streamline processes, and build a strong foundation for secure operations.


## 🛡️ Design
[Design a Gradual Path Towards Immutability](./best-practices/gradual-immutability-path.md)

[Conduct an Actor-Based Threat Modeling](./best-practices/actor-based-threat-modeling.md)

[Follow the Principle of Least Privilege](./best-practices/least-privilege.md)

[Establish a Role-Based Access Control (RBAC) Model](./best-practices/rbac.md)

[Design for Funds Isolation](./best-practices/design-for-funds-isolation.md)

[Consider Deploying Circuit Breakers](./best-practices/circuit-breakers.md)

[Global Registry for Project Deployed Smart Contracts](./best-practices/global-registry.md)

## 🛡️ Coding
[Code Conservatism: Less is More](./best-practices/code-conservatism.md)

[Use a Spell Checker](./best-practices/use-spell-checker.md)

[Use an Up To Date Compiler Version](./best-practices/use-up-to-date-compiler-version.md)

[Security Driven Development](./best-practices/security-driven-development.md)

[Define a Security-Oriented CI Environment](./best-practices/security-oriented-ci.md)

[Prefer Unstructured Storage for Upgradeable Contracts](./best-practices/unstructured-storage.md)

[Avoid Vendoring Dependencies](./best-practices/avoid-vendoring.md)

[Use a Plugin for Safe Upgrades](./best-practices/plugin-for-safe-upgrades.md)

[Use Reentrancy Guards](./best-practices/reentrancy-guards.md)

[Revert/Return Early](./best-practices/revert-return-early.md)

[Avoid Unlimited ERC-20 Approvals](./best-practices/avoid-unlimited-erc20-approvals.md)

[Use the Safe ERC-20 Library](./best-practices/safe-erc20-library.md)

[Use the SafeCast Library](./best-practices/safe-cast-library.md)

[Use Cryptographic Libraries](./best-practices/use-cryptographic-libs.md)

[Prefer to Avoid Low Level Calls](./best-practices/avoid-low-level-calls.md)

[Use `abi.encodeCall()` for Low Level Calls](./best-practices/abi-encode-call.md)

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

[Conduct End to End Testing on Testnet](./best-practices/e2e-tests-testnet.md)

## 🛡️ Pre Deployment
[How to Decide What Type of Security Review Your Project Needs](./best-practices/types-of-security-reviews.md)

[Key Considerations for Setting the Mainnet Deployment Date](./best-practices/setting-the-mainnet-deployment-date.md)

[Conduct an Internal Security Review](./best-practices/internal-security-reviews.md)

[The Importance of Code Freeze Before an External Security Review](./best-practices/importance-of-code-freeze-before-an-external-review.md)

[Conduct an External Security Review (A.K.A Audit)](./best-practices/external-security-reviews.md)

[Implement Robust Monitoring Security Rules](./best-practices/monitoring-security-rules.md)

[Leverage Security Reviews to Define Tailor-Made Monitoring Security Rules](./best-practices/tailor-made-security-rules.md)

[The Importance of Code Freeze Before Deployment](./best-practices/importance-of-code-freeze-before-deployment.md)

[Establish a Contingency Plan](./best-practices/establish-contingency-plan.md)

## 🛡️ Deployment
[Adopt a "Soft Launch" Strategy](./best-practices/soft-launch.md)

[Never Deploy Code That Was Not Reviewed Externally](./best-practices/never-deploy-without-review.md)

[Verify Your Deployed Contracts](./best-practices/post-deployment-verification.md)

[Launch a Bug Bounty Program](./best-practices/bug-bounty.md)

## 🛡️ Ongoing Upgrades
[Handling Communications Before a Smart Contract Upgrade](./best-practices/handling-comms-upgrade.md)

[Ensure Changes are Backwards Compatible](./best-practices/upgrade-backwards-compatibillity.md)

[Use Existing Unit Tests to Prevent Regression Bugs](./best-practices/prevent-regression-bugs.md)

[Handling State Migration in a Secure Way](./best-practices/handling-migartions.md)

[Key Considerations for the Security Review of Upgrades](./best-practices/key-considerations-upgrade-reviews.md)

## 🛡️ Ongoing Operations
[Establish a Chief of Security Role](./best-practices/chief-of-security.md)

[Establish a Security Council](./best-practices/security-council.md)

[Managing Privileged Accounts Securely](./best-practices/securing-privileged-accounts.md)

[Add Regression Tests After Fixing Vulnerabilities](./best-practices/regression-tests-for-vulns.md)

## 🛡️ Emergency Response
[Handling a Security Incident](./best-practices/handling-security-incident.md)

[Post-Incident Actions](./best-practices/post-incident-actions.md)
