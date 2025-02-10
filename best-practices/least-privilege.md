## Principle of Least Privilege

### Overview
Keeping your smart contract functions secure is crucial. By default, public functions should be restricted to prevent unauthorized access and potential exploits. Only specific roles, contracts, or addresses that truly need access should be allowed. Before making any function public, take the time to review its necessity and security implications.

### Best Practices
#### 1. Use Role-Based Access Control (RBAC)
RBAC helps ensure that only the right people (or contracts) can call specific functions. Assign roles carefully and always ask: "Does this role truly need access to this function?"

#### 2. Restrict Access by Default
The safest approach is to lock down all functions unless there’s a strong reason to expose them. If a function must be public, carefully review its security impact before opening it up.

#### 3. Define and Enforce Roles Clearly
Clearly define roles like `ADMIN`, `OPERATOR`, or `USER` and ensure they only have the permissions they need. Avoid broad permissions that could lead to unexpected security risks.

#### 4. Regularly Review and Update Permissions
Access control isn’t a one-time setup—it needs ongoing maintenance. Periodically check function permissions to ensure they still make sense. If a role no longer needs access, revoke it immediately.

### Conclusion
By default, restrict function access and carefully manage permissions using RBAC. Always question whether a function truly needs to be public and regularly review access rights to keep your smart contracts secure.