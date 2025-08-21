## Ensure Code Dependencies Are Secured

### Overview

Solidity projects rely heavily on external libraries (e.g., OpenZeppelin, Uniswap libraries). While these dependencies save development time, they **introduce potential attack surfaces** if versions are not managed carefully.

This document explains how to **pin dependencies** and ensure the version used is **exactly the one audited**, with all known issues addressed.

### 1. Pin Exact Versions

Always pin the exact dependency version in your project configuration instead of using floating versions.

**Examples:**

**Foundry:** (`foundry.toml`):

```toml
[dependencies]
openzeppelin-contracts = { git = "https://github.com/OpenZeppelin/openzeppelin-contracts", tag = "v4.9.3" }
```

**Solidity import:**

```solidity
import "@openzeppelin/contracts@4.9.3/token/ERC20/ERC20.sol";
```

**Why:**

- Prevents accidental upgrades that could introduce vulnerabilities.
- Ensures the audited code matches what is deployed.


### 2. Audit Version Verification

- Security audits **must specify the exact version** or commit audited.
- Before deployment, confirm:
  1. The deployed dependency version matches the audited version.
  2. Any known vulnerabilities from previous audits are patched.

**Tip:** Treat any code change in a dependency as **a new audit scope**.


### 3. Immutable vs Upgradeable Contracts

- **Immutable contracts:** Dependency version must be final; any fixes require redeployment.
- **Upgradeable contracts:** Dependency can be upgraded, but still pin versions and monitor for vulnerabilities.