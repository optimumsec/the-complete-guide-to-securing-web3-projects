## Protect Against Social Media Takeovers (Twitter, Discord)

### Description
Social media takeovers occur when attackers gain unauthorized access to a Web3 project’s Twitter, Discord, or other community accounts. This is usually done through **phishing, credential stuffing, malware on admin devices, or compromised moderator accounts**. Once inside, attackers post malicious links, fake announcements, or false giveaways designed to trick users into connecting wallets to malicious contracts.

### Why It’s Common in Web3
- Web3 projects depend heavily on **Twitter and Discord** for direct communication with their communities.  
- Announcements on these platforms are often **time-sensitive and trusted**, making it easy for attackers to mislead users quickly.  
- Community members are used to seeing links to dApps, airdrops, and token claims—making it harder to detect malicious posts.  

Because of this reliance, a **single compromised account** can result in widespread damage before the breach is noticed.

### Impact
- **Wallet Drains & Phishing**: Users may connect wallets to attacker-controlled contracts.  
- **Scams & False Giveaways**: Fake airdrops or token claims trick users into sending funds or approving malicious contracts.  
- **Community Trust Erosion**: Even after the breach is resolved, trust in the project may be permanently damaged.  
- **Operational Chaos**: Security teams must scramble to warn users, restore control, and clean up reputational harm.  

### Real-World Example
In **2023, Azuki’s official Twitter account** was compromised. The attackers posted a malicious link disguised as a legitimate airdrop. Community members who clicked the link and connected wallets had funds stolen. The event showed how **high-value NFT and token projects are prime targets for social media takeovers**.

### Mitigation Strategies

#### 1. Account Security
- **Strong Authentication**:
  - Use **hardware security keys (FIDO2/WebAuthn)** for Twitter and Discord logins.
  - Avoid SMS-based 2FA, which is vulnerable to SIM-swapping.
- **Separate Accounts**:
  - Do not use personal accounts for project admin roles.
  - Create **dedicated, secured admin accounts** with restricted privileges.
- **Password Hygiene**:
  - Enforce strong, unique passwords stored in a **password manager**.
  - Rotate passwords after role changes or suspected leaks.

#### 2. Access Controls
- **Role-Based Access**:
  - Limit admin and moderator permissions to only what is necessary.
  - Regularly audit who has elevated access to Twitter, Discord, and connected tools.
- **Offboarding**:
  - Immediately remove access from team members or moderators who leave the project.
- **API & Bot Security**:
  - Secure API tokens and bots connected to Discord/Twitter.
  - Avoid running bots from personal accounts.

#### 3. Infrastructure Hardening
- **Device Security**:
  - Ensure all admins use updated operating systems and browsers.
  - Require endpoint protection (antivirus, firewall, anti-malware) on devices used for social media access.
- **Network Hygiene**:
  - Avoid logging in from shared or public networks.
  - Use **VPNs** or dedicated IPs for admin logins.

#### 4. Monitoring & Detection
- **Unusual Activity Alerts**:
  - Enable login alerts for all admin accounts.
  - Monitor for changes in linked apps or integrations.
- **Continuous Monitoring**:
  - Set up automated tools to detect suspicious or unauthorized posts.
  - Encourage community reporting of suspicious activity quickly.

#### 5. User-Facing Precautions
- **Verified Announcements**:
  - Maintain an **official website "announcement board"** as the ultimate source of truth.
  - Cross-post announcements on multiple trusted channels to reduce reliance on one platform.
- **Education**:
  - Train users to **never enter seed phrases or private keys into a website** linked from social media.
  - Encourage the community to verify announcements before interacting.
- **Emergency Communication**:
  - Prepare fallback communication channels (e.g., project blog, GitHub, secondary Twitter/Discord) in case primary accounts are compromised.

### Summary
Social media accounts are often the **front line of trust** for Web3 communities, making them lucrative targets for attackers. A single takeover can lead to **wallet drains, scams, and long-lasting reputational damage**.  

**Mitigation requires a layered defense**: strong authentication, strict access controls, secure devices, continuous monitoring, and clear user education. Projects should also maintain **redundant, verifiable communication channels** so that even if Twitter or Discord is compromised, the community can quickly verify which announcements are authentic.