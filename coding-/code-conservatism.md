## Code Conservatism: Less is More

**Principle:**  
When writing smart contracts, embrace code conservatism: avoid unnecessary complexity. Adding more code doesn't always mean better security. Over-engineering with extra checks or invariants can introduce a false sense of security and increase the risk of unintended consequences, such as unexpected reverts or edge cases that worsen contract reliability.

---

### Why Code Conservatism Matters

1. **Reduced Attack Surface:**  
   - More code means more potential vulnerabilities.  
   - Every line should serve a critical purpose.

2. **False Sense of Security:**  
   - Adding extra invariants or checks can feel like increasing security but may instead:  
     - Create untested failure paths.  
     - Introduce conditions that trigger unexpected reverts.

3. **Audit Complexity:**  
   - Simplicity enhances readability and makes code easier to audit thoroughly.

---

### Actionable Practices

- **Avoid Over-engineering:**  
  - Question every line of code. Does it **truly** contribute to security or essential functionality?

- **Minimize State Changes:**  
  - Limit external state modifications and interactions.

- **Invariants and Assertions:**  
  - Use only essential invariants directly tied to contract integrity.  
  - Avoid excessive runtime checks unless absolutely necessary.

- **Fail Fast, Fail Clearly:**  
  - When adding reverts, ensure they are predictable and do not block valid user interactions.

- **Iterative Review:**  
  - Continuously refactor and simplify.  
  - If a piece of code seems redundant or marginal, reconsider its necessity.

---

### Summary
* Less is more: Write only what's necessary for correctness and security.
* Avoid bloat: More code ≠ more secure.
* Think critically: Don't let additional checks create a false sense of security.