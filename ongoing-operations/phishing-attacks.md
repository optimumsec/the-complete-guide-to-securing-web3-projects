## Protect Against Phishing Attacks

### Description
Phishing attacks in Web3 involve creating **fake websites, emails, or messages** designed to trick victims into revealing sensitive information. The end goal is often to steal **private keys, seed phrases, admin credentials, or API tokens**, enabling attackers to drain wallets or compromise infrastructure.  

Phishing comes in two primary forms:  
1. **Against Users** – Trick community members into connecting wallets or exposing keys.  
2. **Against the Project** – Target team members, admins, or service providers to gain access to project infrastructure (e.g., Discord, Twitter, cloud hosting, code repositories, or treasury funds).  

### Why It’s Common in Web3
- **User Responsibility**: Users directly manage their wallets, making them prime phishing targets.  
- **Centralized Weak Points**: Despite decentralization, projects still rely on centralized services (Twitter, Discord, registrar accounts, GitHub, treasury management dashboards) that can be phished.  
- **Low Cost for Attackers**: Registering fake domains, setting up lookalike websites, or sending convincing DMs costs little.  
- **High Trust Environment**: Communities trust announcements and quick actions (airdrop claims, mint launches), which attackers exploit.  

### Impact
- **User Losses**:
  - Seed phrases or private keys stolen → wallets drained.  
  - Malicious approvals signed → funds compromised.  
- **Project Compromise**:
  - Admin or developer credentials stolen → infrastructure breaches.  
  - Access to **code repositories, treasury funds, or cloud services** → attackers can modify contracts, drain funds, or post malicious content.  
  - Social media or communication platform takeovers → widespread scams posted.  
- **Reputation Damage**: Users often blame the project even when only phishing was involved.  
- **Community Fatigue**: Constant scams lower engagement and trust in legitimate updates.  

### Real-World Examples
- **Against Users**: Fake **MetaMask phishing sites** that prompt users to enter seed phrases, leading to complete wallet compromise.  
- **Against Projects**: In **2023, several Discord admin accounts were phished** via fake “verification” bots, allowing attackers to post malicious links in official project servers. Other attacks have targeted **developer GitHub accounts or treasury management dashboards**, leading to fund losses or malicious contract deployments.  

### Types of Phishing in Web3


#### 1. Phishing Against Users
Attackers attempt to deceive community members directly by impersonating the project.  
**Common tactics include**:  
- Fake airdrop or mint websites.  
- Lookalike domains (typosquatting).  
- Fake Twitter/Discord accounts impersonating the project.  
- Malicious DMs from impersonated admins.  

#### 2. Phishing Against the Project
Attackers target the team itself to gain privileged access to **critical infrastructure or assets**.  
**Common tactics include**:  
- Fake “support” or “KYC” emails to project admins.  
- Phishing pages mimicking registrar, CDN, or cloud providers.  
- Fake Discord/Twitter “verification” messages tricking moderators.  
- Compromising third-party service accounts (analytics, monitoring tools, SaaS).  
- **Access to code repositories** (GitHub/GitLab) → malicious contract deployment or backdoors.  
- **Access to treasury funds** (multisigs, wallets) → direct fund theft.  
- **Access to project infrastructure** (hosting dashboards, API keys, backend servers) → tampering with dApp logic or sensitive data.  


### Mitigation Strategies

#### 1. Protecting Users
- **Domain Security**:
  - Register lookalike domains in advance.  
  - Use **DNSSEC** to secure legitimate domains.  
- **Verified Links**:
  - Pin official websites and contract addresses in multiple channels.  
  - Host a **single "official links" page** that always lists trusted domains.  
- **Community Education**:
  - Educate users: **Never share seed phrases or private keys**.  
  - Encourage bookmarking of official domains.  
  - Train users to always verify transaction details before signing.  
- **Monitoring & Takedowns**:
  - Monitor for fake domains and phishing sites.  
  - Work with registrars and hosting providers for rapid takedowns.  

#### 2. Protecting the Project
- **Admin Account Security**:
  - Enforce **hardware security keys** for logins to registrar, Twitter, Discord, GitHub, cloud services, treasury dashboards.  
  - Avoid SMS-based 2FA (vulnerable to SIM swaps).  
- **Access Control**:
  - Use role-based permissions (least privilege principle).  
  - Audit admin/moderator accounts regularly.  
  - Offboard immediately when roles change.  
- **Anti-Phishing Training**:
  - Educate team members on spear-phishing tactics.  
  - Train admins to verify requests through a second trusted channel before acting.  
- **Infrastructure Safeguards**:
  - Use dedicated project-owned accounts (not personal ones).  
  - Apply strict monitoring and alerts for account logins and changes.  
  - Store API keys and secrets securely (never in plaintext or public repos).  

#### 3. Emergency Response
- **If Users Are Targeted**:
  - Immediately warn the community via all official channels.  
  - Share the malicious domains or addresses being used.  
  - Provide guides for revoking malicious approvals.  
- **If Project Is Targeted**:
  - Revoke compromised credentials or tokens immediately.  
  - Lock down breached platforms (Twitter/Discord, cloud services, GitHub) and post warnings once access is regained.  
  - Review **code repositories, treasury wallets, and backend logs** for signs of tampering.  
  - Conduct a post-mortem and communicate transparently with the community.  


### Summary
Phishing remains the **number one attack vector in Web3**, exploiting human trust rather than smart contract flaws. Both **users** and **projects** are frequent targets: users risk losing funds directly, while projects risk having **critical infrastructure, code, and treasury funds** hijacked to spread scams or manipulate contracts.  

**Mitigation requires defense on two fronts**:  
- **User protection**: education, domain security, and rapid takedowns.  
- **Project protection**: strict access controls, hardware-backed authentication, and phishing-resistant team practices.  

By preparing layered defenses and assuming phishing attempts are inevitable, projects can significantly reduce their community’s exposure and long-term risk.