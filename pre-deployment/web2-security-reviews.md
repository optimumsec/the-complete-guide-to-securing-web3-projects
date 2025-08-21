## Conduct an External Web2 Security Review

While most security reviews in Web3 focus on smart contracts, decentralized applications (dApps) also rely heavily on **traditional Web2 components** such as JavaScript/TypeScript frontends, Python or Node.js backends, and API services. A Web2 code audit reviews these off-chain components for security flaws.

### What a Web2 Code Audit Covers

- **Frontend applications**
  - Secure use of wallet integrations (Metamask, WalletConnect, etc.)
  - Handling of transaction construction logic
  - Prevention of client-side vulnerabilities (e.g., XSS, unsafe eval, DOM injection)
- **APIs and backend services**
  - Authentication and session management
  - Data validation and sanitization
  - Secure API design and rate-limiting
- **Dependency and package security**
  - Insecure npm/pip packages
  - Typosquatted or malicious libraries
  - Unmaintained dependencies with known CVEs
- **Secret and key management**
  - API keys and private keys exposed in code or `.env` files
  - Misconfigured access controls in cloud services