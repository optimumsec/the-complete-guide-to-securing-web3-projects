## Add Regression Tests After Fixing Vulnerabilities

Whether a vulnerability is found during a **security review** or after deployment, it's important to write a test that **simulates the exploit attempt** and verifies it **fails (reverts)** after the fix. This helps:

- Prevent future regressions of the same vulnerability.
- Document the exploit in a reproducible and testable way.
- Strengthen long-term security through test coverage.

> ⚠️ **Limitation**: These tests typically cover only one exploit path. Variations may still exist that trigger the same underlying flaw.

### ✅ Recommendations to Strengthen This Practice:
- **Generalize the test** to detect similar exploit vectors.
- **Write invariant tests** to enforce critical safety conditions across a wide input space.
- **Use property-based fuzzing tools** to explore unseen inputs.
- **Document assumptions** (e.g., actor roles, balances, states) within the test.

This layered approach helps secure the fix and future-proofs the protocol against regressions of the same bug class.