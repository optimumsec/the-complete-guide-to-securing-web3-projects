## Protect Against DNS Poisoning

### Description
DNS Poisoning (also called DNS Hijacking) occurs when attackers manipulate DNS records to redirect users from a legitimate Web3 project’s website to a malicious one. In these attacks, users believe they are interacting with the authentic project interface, but are instead exposed to phishing sites designed to steal **private keys, seed phrases, credentials, or funds**.

Attackers typically achieve this by:
- Compromising the registrar account controlling the project’s domain.
- Exploiting vulnerabilities or misconfigurations in DNS servers.
- Injecting malicious DNS cache entries at the resolver level.

### Why It’s Common in Web3
Web3 projects heavily rely on web frontends for:
- Wallet connections (e.g., MetaMask, WalletConnect).
- Token sales and airdrop participation.
- Project dashboards, staking platforms, and governance portals.

Unlike on-chain smart contracts, DNS remains a **centralized weak point**. A single registrar account or DNS record compromise can redirect massive amounts of traffic to an attacker’s controlled site. Because users are accustomed to trusting a project’s primary domain, these attacks are both **high-impact and high-success**.

### Impact
- **Phishing & Wallet Drains**: Users may unknowingly connect wallets to malicious contracts.
- **Credential Theft**: Login details for admin dashboards, Discord/Telegram, or analytics services may be stolen.
- **Loss of Funds**: Redirected users may approve malicious transactions or send funds to attacker-controlled addresses.
- **Reputation Damage**: Even a short DNS hijack can significantly damage trust in a project.

### Real-World Example
In **2022, Curve Finance** experienced a DNS hijacking attack. Users visiting their legitimate domain were redirected to a fake interface that mimicked Curve’s frontend. This led to users signing malicious approvals and losing funds. The incident highlighted how **DNS remains a bottleneck for Web3 security**.

### Mitigation Strategies

#### 1. Domain & DNS Security
- **Registrar Account Security**:
  - Use **hardware security keys** (e.g., YubiKeys) and **2FA** for registrar logins.
  - Restrict account access to essential personnel only.
  - Regularly review registrar account activity and enable notifications for changes.
- **DNSSEC (Domain Name System Security Extensions)**:
  - Enable **DNSSEC** to cryptographically sign DNS records, reducing the risk of tampering.
  - Work with registrars and DNS providers that support DNSSEC.
- **Reputable DNS Providers**:
  - Use enterprise-grade DNS providers with strong security practices.
  - Avoid free/low-tier providers for critical domains.

#### 2. Infrastructure Hardening
- **Web Hosting & CDN**:
  - Use **cloud providers with DNS-level security features** (e.g., Cloudflare, AWS Route 53).
  - Configure **DNS change alerts** and monitoring for unauthorized modifications.
- **Subdomain Protection**:
  - Audit and clean up unused subdomains to prevent subdomain takeovers.
  - Apply strict CNAME/A record controls.

#### 3. Monitoring & Detection
- **Continuous Monitoring**:
  - Use DNS monitoring tools to detect unauthorized record changes.
  - Monitor SSL/TLS certificate issuance for your domains via [Certificate Transparency logs](https://crt.sh/).
- **Phishing Detection**:
  - Monitor for domains similar to your project’s (typosquatting).
  - Preemptively register commonly mistyped versions of your domain.

#### 4. User-Facing Precautions
- **Official Communication**:
  - Always communicate verified official links via **multiple trusted channels** (Twitter, Discord, GitHub, etc.).
  - Pin verified contract addresses and domains in community channels.
- **Browser Security**:
  - Encourage users to bookmark your official domain.
  - Educate users about **never entering seed phrases or private keys into a website**.
- **Fallbacks**:
  - Provide IPFS-hosted or ENS-linked frontends as **decentralized access points**.
  - Example: Hosting dApp frontends on **ENS + IPFS** ensures users have a verifiable, tamper-resistant alternative.

### Summary
While smart contracts themselves may be immutable and secure, **DNS remains a centralized Achilles’ heel for Web3 projects**. A single lapse in DNS or registrar security can lead to devastating consequences, including stolen funds and loss of community trust.  

**Mitigation requires a layered approach**: registrar account hardening, DNSSEC, enterprise-grade providers, proactive monitoring, and user education. For projects aiming for long-term resilience, offering decentralized frontend alternatives (ENS/IPFS) should be considered a best practice.