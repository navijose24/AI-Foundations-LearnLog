## 🧩 **Unification Algorithm (to find the MGU)**

### 🎯 **Goal:**

Find a substitution (set of variable assignments) that makes two expressions *identical*.

---

### ⚙️ **Algorithm Steps**

| Step                                     | Description                                                                                                                                                        |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **1. Input:**                            | Two expressions (e.g. predicates, terms) E₁ and E₂.                                                                                                                |
| **2. Initialize:**                       | Substitution set θ = {} (empty).                                                                                                                                   |
| **3. Compare structures:**               | If E₁ and E₂ are identical → return θ.                                                                                                                             |
| **4. If one is a variable:**             | - If variable doesn’t occur in the other expression (avoid self-reference), then add substitution {var/value} to θ.<br>- Apply substitution θ to both expressions. |
| **5. If both are compound expressions:** | - Their predicate symbols must match.<br>- Unify their arguments pairwise recursively.                                                                             |
| **6. If none of these cases apply:**     | → Fail (no unification possible).                                                                                                                                  |
| **7. Return:**                           | The final substitution θ as the **MGU**.                                                                                                                           |

---

### ✨ **Example**

Unify:
`Knows(John, x)` and `Knows(y, z)`

**Step 1:** Compare predicates → both “Knows” ✅
**Step 2:** Compare arguments one by one

* John ↔ y → {y/John}
* x ↔ z → {z/x}

Combine:
**θ = {y/John, z/x}** → ✅ This is the MGU.

---

### ⚡ **Example 2:**

Unify `Loves(x, x)` and `Loves(John, Mary)`

→ Compare first arg: {x/John}
→ Apply to second arg: x becomes John
Now we must unify John with Mary ❌ (fails — different constants)

So unification fails → **No MGU exists**.

---

### 🏁 **Summary:**

> The **Unification Algorithm** finds the **Most General Unifier (MGU)** — the smallest substitution set that makes two logical expressions identical. It is essential for Resolution in First Order Logic.

---

