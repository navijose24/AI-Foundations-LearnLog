## 🧩 **Resolution in First Order Logic**

### 💡 **Why it’s needed**

In propositional logic, resolution is easy — no variables, just constants.
But in **FOL**, we have **quantifiers and variables** — things like:

> ∀x [Human(x) → Mortal(x)]

So, we need an advanced version of resolution that can handle variables — that’s **FOL Resolution**.

---

## 🧠 **Core Idea**

Resolution in FOL proves that:

> If (KB ⊨ α), then (KB ∧ ¬α) must be **unsatisfiable** (i.e., lead to a contradiction).

So we **add the negation of the goal** to the KB and try to derive a contradiction (∅).

---

## ⚙️ **Steps in the Resolution Process**

| Step  | Action                                       | Description                                                                                        |
| ----- | -------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **1** | **Convert to CNF (Conjunctive Normal Form)** | All statements in KB + ¬Goal are converted into CNF.                                               |
| **2** | **Eliminate Implications (→)**               | Replace (A → B) with (¬A ∨ B).                                                                     |
| **3** | **Move Negations Inward**                    | Use De Morgan’s laws and quantifier negation (¬∀x ≡ ∃x¬, ¬∃x ≡ ∀x¬).                               |
| **4** | **Standardize Variables**                    | Rename variables so each quantifier has its own variable.                                          |
| **5** | **Skolemization**                            | Remove existential quantifiers by replacing them with Skolem constants/functions.                  |
| **6** | **Drop Universal Quantifiers**               | Once only ∀ remains, drop them (assumed universal).                                                |
| **7** | **Distribute ∨ over ∧**                      | To get a conjunction of disjunctions (CNF form).                                                   |
| **8** | **Resolution Rule**                          | Resolve pairs of clauses that contain complementary literals using **MGU (Most General Unifier)**. |
| **9** | **Continue until**                           | Either empty clause (∅) → goal proven ✅ or no new clause → fail ❌.                                 |

---

## ✨ **Example (Step-by-Step)**

### Given:

1️⃣ ∀x [Human(x) → Mortal(x)]
2️⃣ Human(Socrates)
Goal: Prove Mortal(Socrates)

---

### Step 1: Negate the goal

¬Mortal(Socrates)

So, KB = {Human(x) → Mortal(x), Human(Socrates), ¬Mortal(Socrates)}

---

### Step 2: Remove implications

¬Human(x) ∨ Mortal(x)

---

### Step 3: CNF Form

Clauses:

1. ¬Human(x) ∨ Mortal(x)
2. Human(Socrates)
3. ¬Mortal(Socrates)

---

### Step 4: Resolution

* Resolve (1) and (2): MGU {x/Socrates}
  → Mortal(Socrates)

* Resolve Mortal(Socrates) with (3):
  → ∅ (empty clause)

✅ Contradiction found → **Goal proved: Mortal(Socrates)**

---

## 🧩 **Why Resolution Works**

It’s based on **proof by contradiction** —
if adding ¬Goal to the KB leads to a contradiction,
then the Goal must be logically true.

---

## 🧾 **Advantages**

* Sound (only derives true conclusions)
* Complete (can derive any valid conclusion)
* Works systematically (good for theorem proving)

---

## ⚠️ **Drawbacks**

* Can generate a huge number of clauses (computationally heavy)
* Requires preprocessing (CNF conversion & Skolemization)

---

## 🏁 **Summary**

> **Resolution in FOL** is a rule of inference that proves statements by refutation.
> It combines pairs of clauses containing complementary literals (via MGU) until an empty clause is derived, proving the goal.
> It is both **sound** and **complete**, forming the basis of **automated theorem proving** in AI.

---

