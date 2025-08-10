# Summary

* [Introduction](README.md)

* [Design](best-practices/design.md)
  * Design a Gradual Path Towards Immutability
  * Conduct an Actor-Based Threat Modeling
  * Follow the Principle of Least Privilege
  * Establish a Role-Based Access Control (RBAC) Model
  * Design for Funds Isolation
  * Consider Deploying Circuit Breakers
  * Global Registry for Project Deployed Smart Contracts

* [Coding](best-practices/coding.md)
  * Code Conservatism: Less is More
  * Use a Spell Checker
  * Use an Up-To-Date Compiler Version
  * Security-Driven Development
  * Define a Security-Oriented CI Environment
  * Prefer Unstructured Storage for Upgradeable Contracts
  * Avoid Vendoring Dependencies
  * Use a Plugin for Safe Upgrades
  * Use Reentrancy Guards
  * Revert/Early Returns
  * Avoid Unlimited ERC-20 Approvals
  * Use the Safe ERC-20 Library
  * Use the SafeCast Library
  * Use Cryptographic Libraries
  * Prefer to Avoid Low-Level Calls
  * Use abi.encodeCall() for Low-Level Calls
  * Careful Vetting of Unchecked Blocks
  * Avoid Arbitrary Low-Level External Calls
  * Follow the EIP-712 Standard for Digital Signatures
  * Vetting Process for External Tokens

* [Testing](best-practices/testing.md)
  * Develop Comprehensive Unit Tests
  * Develop Comprehensive Integration Tests
  * Develop Comprehensive Fuzzing Tests
  * Develop Comprehensive Fork Tests
  * Track and Optimize Test Coverage
  * Conduct End-to-End Testing on Testnet

* [Pre-Deployment](best-practices/pre-deployment.md)
  * How to Decide What Type of Security Review Your Project Needs
  * Key Considerations for Setting the Mainnet Deployment Date
  * Conduct an Internal Security Review
  * The Importance of Code Freeze Before an External Security Review
  * Conduct an External Security Review (a.k.a. Audit)
  * Implement Robust Monitoring Security Rules
  * Leverage Security Reviews to Define Tailor-Made Monitoring Rules
  * Establish a Contingency Plan

* [Deployment](best-practices/deployment.md)
  * Adopt a “Soft Launch” Strategy
  * Never Deploy Code That Was Not Reviewed Externally
  * Verify Your Deployed Contracts
  * Launch a Bug Bounty Program

* [On-Going Upgrades](best-practices/upgrades.md)
  * Handling Communications Before a Smart Contract Upgrade
  * Ensure Changes Are Backwards Compatible
  * Use Existing Unit Tests to Prevent Regression Bugs
  * Handling State Migration in a Secure Way
  * Key Considerations for the Security Review of Upgrades

* [On-Going Operations](best-practices/operations.md)
  * Establish a Chief of Security Role
  * Establish a Security Council
  * Managing Privileged Accounts Securely
  * Add Regression Tests After Fixing Vulnerabilities

* [Emergency Response](best-practices/emergency-response.md)
  * Handling a Security Incident
  * Post-Incident Actions

* [About & Resources](README.md)
