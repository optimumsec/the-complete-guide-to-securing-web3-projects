
* [The Complete Guide to Securing Web3 Protocols](gitbook-README.md)

* Design
  * [Design a Gradual Path Towards Immutability](design/gradual-immutability-path.md)
  * [Actor-Based Threat Modeling](design/actor-based-threat-modeling.md)
  * [Principle of Least Privilege](design/least-privilege.md)
  * [Implement a Role-Based Access Control (RBAC) Model](design/rbac.md)
  * [Design for Funds Isolation](design/funds-isolation.md)
  * [Implement Circuit Breakers](design/circuit-breakers.md)
  * [Global Registry for Project Deployed Smart Contracts](design/global-registry.md)

* Coding
  * [Code Conservatism: Less is More](coding/code-conservatism.md)
  * [Use a Spell Checker](coding/use-spell-checker.md)
  * [Use an Up-To-Date Compiler Version](coding/use-up-to-date-compiler-version.md)
  * [Security-Driven Development](coding/security-driven-development.md)
  * [Define a Security-Oriented CI Environment](coding/security-oriented-ci.md)
  * [Prefer Unstructured Storage for Upgradeable Contracts](coding/unstructured-storage.md)
  * [Avoid Vendoring Dependencies](coding/avoid-vendoring.md)
  * [Use a Plugin for Safe Upgrades](coding/plugin-for-safe-upgrades.md)
  * [Use Reentrancy Guards](coding/reentrancy-guards.md)
  * [Revert/Return Early](coding/revert-return-early.md)
  * [Avoid Unlimited ERC-20 Approvals](coding/avoid-unlimited-erc20-approvals.md)
  * [Use the Safe ERC-20 Library](coding/safe-erc20-library.md)
  * [Use the SafeCast Library](coding/safe-cast-library.md)
  * [Use Cryptographic Libraries](coding/use-cryptographic-libs.md)
  * [Prefer to Avoid Low-Level Calls](coding/avoid-low-level-calls.md)
  * [Use `abi.encodeCall` for Low Level Calls](coding/abi-encode-call.md)
  * [Careful Vetting of Unchecked Blocks](coding/careful-vetting-of-unchecked-blocks.md)
  * [Avoid Arbitrary Low-Level External Calls](coding/avoid-arbitrary-external-calls.md)
  * [Follow the EIP-712 Standard for Digital Signatures](coding/adhere-to-eip-712.md)
  * [Vetting Process for External Tokens](coding/vetting-process-for-external-tokens.md)

* Testing
  * [Develop Comprehensive Unit Tests](testing/unit-tests.md)
  * [Develop Comprehensive Integration Tests](testing/integration-tests.md)
  * [Develop Comprehensive Fuzzing Tests](testing/fuzzing-tests.md)
  * [Develop Comprehensive Fork Tests](testing/fork-tests.md)
  * [Track and Optimize Test Coverage](testing/optimize-test-coverage.md)
  * [Conduct End-to-End Testing on Testnet](testing/e2e-tests-testnet.md)

* Pre-Deployment
  * [How to Decide What Type of Security Review Your Project Needs](pre-deployment/types-of-security-reviews.md)
  * [Key Considerations for Setting the Mainnet Deployment Date](pre-deployment/setting-the-mainnet-deployment-date.md)
  * [Conduct an Internal Security Review](pre-deployment/internal-security-reviews.md)
  * [The Importance of Code Freeze Before an External Security Review](pre-deployment/importance-of-code-freeze-before-an-external-review.md)
  * [Conduct an External Security Review (a.k.a. Audit)](pre-deployment/external-security-reviews.md)
  * [Implement Robust Monitoring Security Rules](pre-deployment/monitoring-security-rules.md)
  * [Leverage Security Reviews to Define Tailor-Made Monitoring Rules](pre-deployment/tailor-made-security-rules.md)
  * [Establish a Contingency Plan](pre-deployment/establish-contingency-plan.md)

* Deployment
  * [Adopt a “Soft Launch” Strategy](deployment/soft-launch.md)
  * [Never Deploy Code That Was Not Reviewed Externally](deployment/never-deploy-without-review.md)
  * [Verify Your Deployed Contracts](deployment/post-deployment-verification.md)
  * [Launch a Bug Bounty Program](deployment/bug-bounty.md)

* Ongoing Upgrades
  * [Handling Communications Before a Smart Contract Upgrade](ongoing-upgrades/handling-comms-upgrade.md)
  * [Ensure Changes Are Backwards Compatible](ongoing-upgrades/upgrade-backwards-compatibillity.md)
  * [Use Existing Unit Tests to Prevent Regression Bugs](ongoing-upgrades/prevent-regression-bugs.md)
  * [Handling State Migration in a Secure Way](ongoing-upgrades/handling-migrations.md)
  * [Key Considerations for the Security Review of Upgrades](ongoing-upgrades/key-considerations-upgrade-reviews.md)

* Ongoing Operations
  * [Establish a Chief of Security Role](ongoing-operations/chief-of-security.md)
  * [Establish a Security Council](ongoing-operations/security-council.md)
  * [Managing Privileged Accounts Securely](ongoing-operations/securing-privileged-accounts.md)
  * [Add Regression Tests After Fixing Vulnerabilities](ongoing-operations/regression-tests-for-vulns.md)

* Emergency Response
  * [Handling a Security Incident](emergency-response/handling-security-incident.md)
  * [Post-Incident Actions](emergency-response/post-incident-actions.md)
