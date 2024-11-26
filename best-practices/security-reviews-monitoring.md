### Leverage Security Reviews to Define Monitoring Security Rules
Involving security researchers in defining monitoring invariants during the security review ensures a more effective and relevant monitoring system. Researchers have a deep understanding of the contract’s logic, edge cases, and vulnerabilities, allowing them to identify critical conditions that should remain true throughout the contract’s lifecycle. This helps detect issues like state inconsistencies or unauthorized actions early, strengthening the link between pre-deployment analysis and post-deployment monitoring.  

Adding this step during the review also saves time and resources. Since researchers are already deeply familiar with the code, they can design monitoring logic without duplicating efforts later. Some risks identified during the review may not be directly fixable in the code but can be addressed with off-chain monitoring, such as tracking unusual access attempts.  

Most standard monitoring tools lack the ability to implement custom rules tailored to a specific contract. Security researchers can fill this gap by creating bespoke rules that address unique risks, such as monitoring for interactions with high-risk addresses or tracking anomalies in critical functions. This tailored approach provides precision and coverage that generic tools often miss."


#### Examples of Security Rules

##### 1. Track Execution of Admin Functions  
**Rule**: Log and monitor all transactions involving admin functions, such as transferring ownership, pausing the contract, or upgrading logic.  

**Rationale**: Admin functions have wide-reaching effects on the contract. Unauthorized or unexpected usage could lead to exploits or governance disputes.  

##### 2. Monitor State Variable Changes  
**Rule**: Continuously validate critical state variables (e.g., owner, whitelists, or key parameters) to ensure they remain as expected.  

**Rationale**: State variables are often targeted by attackers to bypass access controls or escalate privileges. Detecting unauthorized changes can prevent escalation.  

##### 3. Validate Oracle Price Feeds  
**Rule**: Compare price feeds from oracles with market norms and redundant oracles to detect sudden deviations.  

**Rationale**: Manipulated oracles can destabilize contracts, resulting in improper liquidations or inaccurate transactions. Monitoring ensures integrity.  



##### 1. Detecting Interactions from Suspicious Sources  

**Rule**: Monitor and flag interactions originating from:  
- Contracts with closed source code.  
- Addresses funded by Tornado Cash or other mixers.  
- Addresses identified as malicious by community threat intelligence or on-chain oracles.  

**Why It Matters**: Interactions from such sources are often linked to exploit attempts. Attackers typically use mixers and anonymized contracts to obscure their tracks, making it crucial to flag these interactions for deeper investigation.  

##### 2. Tracking Transactions Involving Flash Loans  

**Rule**: Detect and analyze transactions that involve flash loans.  

**Why It Matters**: While not inherently malicious, flash loans are often used by attackers. Their use demands closer scrutiny to uncover potential threats hidden in complex transaction sequences.  

##### 3. Monitoring Abnormal Balance Fluctuations  

**Rule**: Define thresholds for balance changes in both native assets and ERC20 tokens. Flag any transactions that result in abnormal or unexpected shifts.  

**Why It Matters**: Sudden or significant changes in a contract’s balance often signal potential exploits, such as unauthorized withdrawals, minting bugs, or value-draining attacks. Real-time detection of these fluctuations enables faster remediation.  

##### 4. Identifying Interactions with Rarely Used Functions  

**Rule**: Track calls to contract functions that are seldom invoked.  

**Why It Matters**: Attackers frequently target obscure or rarely used functions that might have been overlooked during development or audits. Monitoring these interactions helps surface unusual activity and ensures these functions are not exploited unnoticed.  

##### 5. Monitoring "Push Payments" for Potential Reverts  

**Rule**: Track and flag reverts during ETH transfers to multiple recipients in a single transaction. Log the specific recipient causing the failure.  

**Why It Matters**: While the "pull" pattern is generally advised for distributing funds due to its resilience to denial-of-service (DoS) risks, many projects opt for the "push" pattern for better user experience. In these cases, privileged users are often allowed to remove problematic recipients, but monitoring for reverts is essential to quickly identify and address potential disruptions.  

##### 7. Detecting Spikes in Failed Transactions  

**Rule**: Monitor the number of failed transactions interacting with the contract over a set time frame. Flag any spikes that exceed normal activity levels.  

**Why It Matters**: A sudden increase in failed transactions can indicate deliberate DoS attacks, bugs in the contract, or malicious usage by attackers. Identifying these spikes early helps mitigate issues before they escalate.  
