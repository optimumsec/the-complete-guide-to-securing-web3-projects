## Vetting Process For External Tokens

When integrating external tokens (such as ERC-20, ERC-721, or ERC-1155) with your system, it's essential to conduct a rigorous vetting process to prevent integration errors and security risks. Begin by thoroughly reviewing the token's code to ensure it complies with the relevant standard and behaves as expected. For instance, some ERC-20 tokens may have centralized controls, blacklists, or transfer restrictions that could lead to unexpected denial-of-service issues within your contract. 

Additionally, certain tokens—like elastic supply tokens or fee-on-transfer tokens—may introduce balance discrepancies due to their unique mechanics, potentially breaking assumptions about balance tracking in your system. Tokens like USDT, which do not return a success value upon transfers, require special handling to ensure transaction outcomes are properly validated.

---

The following checklist outlines the key aspects to verify when reviewing an ERC-20 token contract:

### 1. **Review Security Audits**
   - Ensure you read the security review of the code thoroughly. This will help identify any potential vulnerabilities or issues that have been previously discovered.
   - Verify that all the issues identified in the security review have been properly addressed and mitigated before integrating the token into your DeFi platform.

### 2. **Basic ERC-20 Functionality**
   - Ensure the token implements the core ERC-20 functions (`totalSupply`, `balanceOf`, `transfer`, `approve`, `allowance`, and `transferFrom`) correctly.
   - Verify that the token emits appropriate events (e.g., `Transfer`, `Approval`) for all relevant actions.

### 3. **Minting and Burning Mechanisms**
   - Confirm that the minting process (if allowed) is strictly controlled. There should be clear access controls to prevent unauthorized minting.
   - If the token is burnable, check that the burn logic is correctly implemented and transparent.
   - Verify that minting and burning are not exploited to manipulate supply or cause inflationary issues.

### 4. **Access Control and Ownership**
   - Check for proper access control mechanisms, especially for functions that could alter the token supply (e.g., `mint`, `burn`, `pause`).
   - Confirm that only authorized addresses (such as the contract owner or a trusted multi-sig wallet) can execute sensitive functions.
   - Ensure the contract owner cannot abuse their privileges (e.g., disabling transfers or minting an excessive amount of tokens).

### 5. **Pausing Mechanism**
   - Verify if the contract implements a pause function and under what circumstances it can be triggered. This should be limited to specific trusted entities and only used in emergencies.
   - Ensure that the pause functionality doesn’t allow for unwanted freezing of token transfers or functionality.

### 6. **Reentrancy and Gas Limits**
   - Ensure that the token contract does not have any external calls that can cause a reentrancy, especially in functions like `transfer` or `approve`.
   - Check for gas heavy functions that might exceed block gas limits and cause a denial of service.

### 7. **Decimals and Precision**
   - Confirm the token’s `decimals` value is set correctly. A common value is 18, but verify if it matches the expected behavior and meets your project’s needs.
   - Make sure the token decimals are appropriately scaled in your system.

### 8. **Permit and EIP-2612 (Optional)**
   - Check if the token supports EIP-2612 (Permit), allowing users to approve tokens via signatures rather than transactions, reducing gas costs in DeFi interactions.
   - Verify that the `permit` function is implemented securely, particularly around signature handling.

### 9. **Transfer Restrictions**
   - Confirm that there are no hardcoded or poorly documented restrictions on transfers (e.g., blacklists, limits on individual transfers) unless required by project rules.
   - If there are any restrictions, ensure they are fully transparent and disclosed to users.

### 10. **Event Emissions and Monitoring**
   - Ensure that the contract emits proper events for all critical actions, such as transfers and approvals.
   - This is crucial for tracking token movements and for integrating the token into your DeFi project with accurate tracking.

### 11. **Ownership and Tokenomics Transparency**
   - Ensure that the tokenomics (e.g., initial supply, distribution, and allocation) are clearly documented and reflect the intended use case of the token.
   - Verify that any special minting or distribution processes are transparent and fair, without leaving room for abuse by insiders or malicious actors.

### 12. **Testing**
   - Ensure the contract has passed thorough testing, including unit tests and integration tests, to catch edge cases and unexpected behaviors.

### 13. **ERC-20 Compliance vs. ERC-777 or Other Token Standards**
   - Verify that the token strictly adheres to the ERC-20 standard and does not introduce unnecessary complexity or incompatibility issues with other DeFi protocols.
   - If the token uses a more complex standard like ERC-777, ensure it doesn’t introduce vulnerabilities, such as reentrancy or unexpected interactions with other contracts.

### 14. **Verify Non-Standard Functions**
   - Review any non-standard functions added to the ERC-20 contract, such as `pause`, `mint`, `burn`, or any custom logic. Ensure these are necessary, transparent, and properly secured.
   - Make sure that non-standard functions are properly documented and do not introduce unnecessary risks.

### 15. **Check for External Dependencies**
   - Confirm that the ERC-20 token does not rely on external contracts or services that could pose a security risk (e.g., external oracles or other on-chain dependencies).
   - If external dependencies exist, verify that they are secure, and their failure won’t jeopardize the token’s functionality or integrity.