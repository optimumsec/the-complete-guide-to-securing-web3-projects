## Verify Your Deployed Contracts

Deploying a smart contract to mainnet is a point of no return — any misconfiguration or overlooked mistake can lead to loss of funds or trust. A robust verification process after deployment ensures that the contract matches the audited code and behaves as expected. Below is a structured guide to verifying a smart contract deployment securely and thoroughly.

---

### Why Deployment Verification?
1. **Ensure Audit Relevance**: Confirm that the deployed contract matches the version that was audited.
2. **Prevent Silent Modifications**: Detect unauthorized or accidental changes between audit and deployment.
3. **Some Misconfigurations Are Invisible in Audit**: There are misconfiguration issues that can't be caught in an audit — they must be verified in the context of a live deployment.

---

### Steps for Deployment Verification

1. **Verify Source Code and Compiler Settings**
   - **Match Bytecode**: Ensure the deployed bytecode corresponds exactly to the audited source code.
   - **Match Compiler Version & Settings**: Confirm that the Solidity compiler version and optimization flags are identical to those used during the audit.
   - **Example**: Use Etherscan’s contract verification UI or a tool like `sourcify.dev` to verify the contract on‑chain.

2. **Verify Final Code Version**
   - **Post‑Fix Deployment**: Confirm that the deployed version contains *all* fixes and patches introduced during and after security reviews.
   - **How**: Cross‑check the Git commit, release tag, or hash used for deployment against the version approved in the final audit report.

3. **Check Constructor Arguments**
   - **What to Look For**: Ensure initialization parameters (e.g., admin addresses, external token addresses, fee rates) are correctly set.
   - **How**: Decode the deployment transaction input or read constructor arguments from block explorers and compare them with audited config files.

4. **Confirm Contract Ownership and Roles**
   - **Ownership, Admin Rights & Role Setup**: Make sure privileged roles are held by the correct addresses or multisigs *and* that role permissions (`AccessControl`, `owner()`, etc.) are correctly configured and verifiable on‑chain.

5. **Validate Upgradeability Setup**
   - **If Using Proxies**: Check that the proxy points to the intended implementation and that the upgrade admin is properly configured.
   - **How**: Inspect storage slots manually or use tools like `openzeppelin‑upgrades` to verify the proxy pattern.

6. **Confirm Deployment Scripts Were Followed**
   - **Replay and Audit the Script**: Ensure the deployment was executed via the approved and audited scripts.
   - **Best Practice**: Automate deployment with reproducible scripts (e.g., Foundry, Hardhat) and record the transaction hashes.

7. **Match Deployed Addresses**
   - **For Multisigs, Tokens, Registries**: Confirm that all deployed contract addresses match those expected in documentation, frontends, and audit reports.
   - **Cross‑check**: Ensure integrations and monitoring systems use the correct addresses.

8. **Enable Public Verification**
   - **Verified Source Code**: Publish the verified source code to public block explorers.
   - **Public README / Audit Link**: Make the audit report and deployment configuration publicly accessible to build user confidence.

9. **Tag the Commit Hash as a Release on GitHub**
   - **Why**: This provides a public, immutable reference to the exact code version that was deployed.

10. **Export Contract Addresses to Your GitHub Repo**
   - **Why**: Keeping deployed addresses in your repository (e.g., as a JSON or markdown file) improves transparency and simplifies integration for users and partners.
   - **Best Practice**: Include network name, contract name, address, and optionally, verification links.
