## External Security Reviews

Engaging external security experts to review the code is crucial for ensuring the robustness of smart contracts and mitigating potential vulnerabilities. Just as the three-way handshake establishes a reliable connection by exchanging critical information, the audit process similarly unfolds in stages. 

The first stage, represented by the **SYN**, corresponds to the issues identified by the security researchers during their initial review. The subsequent **SYN-ACK** phase involves the development team implementing fixes based on the security researchers' findings. Finally, the **ACK** phase signifies the security researchers verifying these fixes, confirming that the issues have been addressed effectively. 

---

### How to Prepare for a Security Review

**Smart contract security is a collaborative effort**. It’s not just the responsibility of security researchers to ensure a codebase is secure—developers play a crucial role too. Both sides need to align on a shared mission: to surface and fix vulnerabilities before they make it to production.

A core principle to understand is that **the main resource in any security review is the time and focus of the researchers**. Reviews are already quite expensive. If researchers are spending their time flagging basic issues, they're not spending that time analyzing complex logic or subtle edge cases that could cause real-world financial loss. **Too many avoidable bugs eat into review time**, and each one takes time to document clearly—especially in professional settings where researchers are expected to produce detailed reports. That reduces the time available to uncover hidden, critical issues.

So how can developers help maximize the value of a security review?

1. **Pick the Right Security Researchers**  
   Choose researchers with the relevant expertise and a proven track record. It's crucial to select professionals you can trust to act ethically and transparently. Look for researchers who specialize in smart contract security and have demonstrated success in similar projects.

2. **Assess the Effort (Time and Budget)**  
   Ask the security researchers to assess the time and budget required for the review. This will ensure you have realistic expectations and resources in place to complete the review and fix any identified issues.

3. **Test Coverage**  
   A high level of test coverage is foundational. We expect at least 90%+ coverage, including statement, branch, and function coverage. But it's not just about raw percentages. You need to test both:  
   - **Happy paths**—the expected flow when everything works as intended.  
   - **Failure paths**—unexpected inputs, edge cases, and revert scenarios.  
   A red flag for us is when the codebase has too many bugs that could’ve easily been caught just by testing happy paths.

4. **Identify Areas of Concern**  
   Prepare a list of areas where you specifically want extra assurance. This can include complex logic, integrations with other contracts, or areas that you know may carry higher risk. By highlighting these areas, you can ensure that the review is focused and efficient.

5. **Test Variety**  
   Unit tests are essential, but not sufficient. You should also include:  
   - **Integration tests** that simulate interactions between components.  
   - **Fork-based tests** using live network state and real token balances.  
   - **Fuzz testing**, where tools like Foundry or Echidna randomly mutate inputs to uncover unexpected behavior.

6. **Allocate Time for Fixes**  
   Pre-allocate sufficient time for addressing any issues found during the review. After the audit, there will be fixes to implement and further testing to conduct. Be sure to budget adequate time for additional tests to ensure everything works as expected before deployment.

7. **Deployment Readiness**  
   We often see projects that delay writing deployment scripts until the very end. That’s a mistake. Security reviewers should be able to review and run your deployment process—ideally in a testnet environment that mimics mainnet settings. Scripts should include:  
   - Configuration options.  
   - Admin setup.  
   - Upgradeability logic, if relevant.  
   Also, testnet deployment and basic real-world interactions—minting tokens, transferring ownership, calling governance—should be working and demonstrable before review starts.

8. [**Internal Review**](./internal-security-reviews.md)
   
   Before handing code over for external security review, it should go through an internal review by developers who didn’t write the code. Fresh eyes often catch obvious flaws and can verify whether the design aligns with the implementation. It also shows that the team takes security seriously.

9. **Documentation**  
   Good documentation saves researchers time and leads to better results. Why? Security researchers need to look for a range of vulnerabilities, including:  
   - **Well-known Solidity issues** (like reentrancy, unsafe math, unchecked return values).  
   - **Common coding mistakes** (off-by-one errors, lack of access control, bad assumptions).  
   - **Economic/MEV vulnerabilities** (price manipulation, oracle misuse, sandwiching opportunities).  
   But that’s not all. Researchers also look for:  
   - **Application-Specific/Business Logic Vulnerabilities**.  
   - **Specification Mismatch Issues**.  
   - **Specification Design Issues**.  
   The better your documentation explains the intended behavior, the easier it is for researchers to catch when the code deviates from that behavior.