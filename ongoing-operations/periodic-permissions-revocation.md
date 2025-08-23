## Periodically Revoke Permissions to Critical Assets

Maintaining tight control over access to critical project assets is a
cornerstone of Web3 security. Over time, collaborators, contractors, or
contributors may leave, and even trusted team members may no longer need
certain privileges. Failing to revoke permissions promptly leaves your
project vulnerable to insider threats, accidental misuse, or credential
compromise.

This guide outlines why revocation is necessary, what assets are most at
risk, and how to implement a healthy revocation and rotation process.


### Why Revocation Matters

-   **Mitigate insider threats** -- Former collaborators may retain
    access unless permissions are actively removed.
-   **Reduce attack surface** -- Exposed keys, dormant accounts, or
    unused permissions increase risk.
-   **Compliance and accountability** -- Many industry standards (e.g.,
    SOC2, ISO27001) require periodic access reviews.
-   **Adaptability** -- Projects evolve, and so should their access
    controls.

### Critical Assets That Require Access Review

1.  **Code Repositories**
    -   GitHub / GitLab / Bitbucket organizations
    -   Repository collaborators, branches, and protected branches
    -   CI/CD integrations and deploy keys
2.  **Smart Contract Deployment & Treasury**
    -   Multisig wallets (e.g., Gnosis Safe, Zodiac, OpenZeppelin
        Defender)
    -   Deployer accounts
    -   Upgrade admin roles
    -   Hardware wallets for signers
    -   Custody provider accounts (exchanges, custodians)
    -   Bridges and staking contracts
3.  **Infrastructure**
    -   Cloud providers (AWS, GCP, Azure)
    -   Hosting services (Vercel, Netlify, Cloudflare, Infura, Alchemy)
    -   Server access (SSH keys, Kubernetes clusters, Docker registries)
4.  **API Keys & Secrets**
    -   RPC providers
    -   Payment processors
    -   External services (analytics, monitoring, bug trackers)
5.  **Operations Tools**
    -   Communication channels (Slack, Discord, Telegram admin roles)
    -   Project management tools (Notion, Jira, Trello)
    -   Security tools (Sentry, monitoring dashboards, SOC integrations)
6.  **Social & Brand Assets**
    -   Twitter / X, Telegram, Discord servers, LinkedIn, Medium
    -   Domain registrar accounts and DNS providers


### Best Practices for Revoking Permissions

-   **Create an Offboarding Checklist**
    Maintain a standardized checklist to revoke all access when a
    collaborator leaves.

-   **Use Role-Based Access Control (RBAC)**
    Assign access based on roles, not individuals, to simplify
    revocation when people change responsibilities.

-   **Automate Where Possible**

    -   Use tools like GitHub Actions, Terraform, or Vault to rotate
        keys on a schedule.
    -   Employ secrets managers (HashiCorp Vault, AWS Secrets Manager,
        Doppler).

-   **Enforce Key Rotation**
    Periodically rotate multisig signers, API keys, and passwords---even
    for active members.

-   **Implement the Principle of Least Privilege**
    Only grant the minimum level of access required for a contributor's
    role.

-   **Schedule Periodic Reviews**
    Conduct quarterly or bi-annual audits of who has access to what.
    Remove unnecessary permissions proactively.

-   **Log and Monitor Access Changes**
    Keep a changelog or use services that track access revocations and
    permission updates for accountability.


### Treasury & Financial Assets

The treasury often represents the majority of a project's funds. Any
compromise here can be catastrophic. Treat access to treasury controls
with the highest level of security and enforce strict revocation and
rotation processes.

#### Best Practices for Treasury Access Management

-   **Rotate Multisig Signers**
    -   Remove signers who leave the team or change roles.
    -   Replace with new trusted members or rotate periodically to limit
        long-term exposure.
    -   Document and communicate the process for signer replacement.
-   **Implement Threshold Adjustments**
    -   Reevaluate signing thresholds after signers are removed.
    -   Ensure the threshold still balances **security** (not too low)
        and **operability** (not too high).
-   **Use Hardware Wallets Only**
    -   Require all signers to use hardware wallets.
    -   Revoke access if a signer loses their device or recovery phrase.
-   **Limit Direct Access**
    -   Avoid keeping funds in EOAs (Externally Owned Accounts).
    -   Use smart contract wallets with granular role management.
-   **Separate Treasury Layers**
    -   Maintain different wallets for operational expenses, payroll,
        and reserves.
    -   Give access only to the relevant wallet, not the entire
        treasury.
-   **Audit Regularly**
    -   Conduct quarterly access reviews of treasury signers.
    -   Verify each signer is active, reachable, and still trusted.
-   **Emergency Rotation Protocol**
    -   Define and rehearse an emergency plan if a signer is compromised
        or unavailable.
    -   Pre-approve backup signers to avoid governance delays in
        critical moments.

------------------------------------------------------------------------

### Example Offboarding Workflow

1.  Remove collaborator from GitHub organization and repositories.
2.  Rotate repository deploy keys and CI/CD secrets.
3.  Remove signer from multisig wallet and replace with a new trusted
    member.
4.  Rotate API keys for critical services (RPC, monitoring, analytics).
5.  Remove access to cloud providers, hosting services, and dashboards.
6.  Remove admin roles from communication platforms.
7.  Update internal access logs.