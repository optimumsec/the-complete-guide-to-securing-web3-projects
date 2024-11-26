## Leverage Security Reviews to Define Tailor-Made Monitoring Security Rules
Involving security researchers in defining monitoring invariants during the security review ensures a more effective and relevant monitoring system. Researchers have a deep understanding of the contract’s logic, edge cases, and vulnerabilities, allowing them to identify critical conditions that should remain true throughout the contract’s lifecycle. This helps detect issues like state inconsistencies or unauthorized actions early, strengthening the link between pre-deployment analysis and post-deployment monitoring.  

Adding this step during the review also saves time and resources. Since researchers are already deeply familiar with the code, they can design monitoring logic without duplicating efforts later. Some risks identified during the review may not be directly fixable in the code but can be addressed with off-chain monitoring, such as tracking unusual access attempts.  

Most standard monitoring tools lack the ability to implement custom rules tailored to a specific contract. Security researchers can fill this gap by creating bespoke rules that address unique risks, such as monitoring for interactions with high-risk addresses or tracking anomalies in critical functions. This tailored approach provides precision and coverage that generic tools often miss.


### Examples of Tailor-Made Security Rules

#### 1. Tracking Calls to Admin Functions  
**Rule**: Log and monitor all transactions involving admin functions, such as transferring ownership, pausing the contract, or upgrading logic.  

**Rationale**: Admin functions have wide-reaching effects on the contract. Unauthorized or unexpected usage could lead to exploits or governance disputes.  

#### 2. Monitoring Certain State Variable Changes  
**Rule**: Continuously validate critical state variables (e.g., owner, whitelists, or key parameters) to ensure they remain as expected.  

**Rationale**: State variables are often targeted by attackers to bypass access controls or escalate privileges. Detecting unauthorized changes can prevent escalation.  

#### 3. Validating Oracle Price Feeds  
**Rule**: Compare price feeds from oracles with market norms and redundant oracles to detect sudden deviations.  

**Rationale**: Manipulated oracles can destabilize contracts, resulting in improper liquidations or inaccurate transactions. Monitoring ensures integrity.  

#### 4. Monitoring "Push Payments" for Potential Reverts  

**Rule**: Track and flag reverts during ETH transfers to multiple recipients in a single transaction. Log the specific recipient causing the failure.  

**Rationale**: While the "pull" pattern is generally advised for distributing funds due to its resilience to denial-of-service (DoS) risks, many projects opt for the "push" pattern for better user experience. In these cases, privileged users are often allowed to remove problematic recipients, but monitoring for reverts is essential to quickly identify and address potential disruptions.  
