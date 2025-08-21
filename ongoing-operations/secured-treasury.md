## Secure Your Treasury

Managing a treasury in a Web3 project is one of the most critical responsibilities for founders, DAOs, and protocol teams. A compromised treasury can lead to devastating losses, damaged reputation, and loss of community trust. This document outlines key practices to **keep your treasury secure**.

---

### Principles of Treasury Safety

- **Minimize single points of failure** — no single individual should have the ability to move all funds.  
- **Defense-in-depth** — combine multiple layers of security (on-chain, off-chain, operational).  
- **Transparency with accountability** — the community should understand how treasury funds are safeguarded and used.  

---

### Key Practices

#### 1. Use Multi-Signature Wallets
- Deploy a **multi-sig (e.g., Gnosis Safe)** for treasury management.  
- Require **at least 2/3 or 3/5 approvals** to move funds.  
- Regularly review signers’ activity and update signer sets when members change.  

#### 2. Role Separation
- Separate **operational wallets** (day-to-day payments) from **treasury wallets** (long-term reserves).  
- Keep treasury funds in a more secure setup with higher signer thresholds.  

#### 3. Access Control and Signer Security
- Signers should use **hardware wallets** (Ledger, Trezor) rather than browser extensions.  
- Enable **passphrase protection and biometric/PIN locks**.  
- Keep seed phrases **offline and geographically distributed**.  

#### 4. On-Chain Safeguards
- Consider **time-lock contracts** for large treasury actions, giving the community time to review before execution.  
- Use **spending limits** for operational wallets to prevent draining in case of compromise.  

#### 5. Diversification of Assets
- Avoid keeping 100% of funds in a single token or chain.  
- Diversify between **stablecoins, ETH, BTC, and protocol-native tokens**.  
- If holding stablecoins, diversify across issuers (USDC, USDT, DAI).  

#### 6. Insurance and Custody Options
- For larger treasuries, explore **crypto insurance** providers.  
- Consider **qualified custodians** if regulatory or institutional requirements apply.  

#### 7. Continuous Monitoring
- Set up **real-time alerts** (e.g., Tenderly, Forta, OpenZeppelin Defender) for unusual transactions.  
- Regularly **audit treasury contracts and signers**.  
- Run **internal drills** to simulate compromised keys or stolen funds.  

#### 8. Governance Security
- If treasury spending is controlled by governance:
  - Use **guarded launch strategies** to avoid malicious proposals.  
  - Employ **veto powers or emergency pause mechanisms**.  
  - Audit the governance contracts regularly.  


### Emergency Planning
- Prepare a **disaster recovery plan**: what happens if a signer is compromised or unavailable?
- Ensure **backup signers** can be onboarded quickly.
- Document procedures for community communication in case of incidents.