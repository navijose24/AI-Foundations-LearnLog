## 🧩 **First Order Logic (FOL)**

### 💡 What it is:

Propositional logic could only say things like

> “It’s raining” or “It’s sunny.”

But it **can’t express relationships** like

> “Every student has a teacher” or “Ravi loves Meera.”

👉 **FOL = Propositional Logic + Quantifiers + Predicates**
It allows AI to represent **objects**, **relations**, and **properties** in the world.

---

## 🧠 1️⃣ **Syntax of FOL (The Structure / Grammar)**

Syntax = *rules of how to write valid FOL sentences*.
Think of it like grammar for logic.

| Symbol          | Meaning                              | Example                               |
| --------------- | ------------------------------------ | ------------------------------------- |
| **Constants**   | Specific objects                     | `John`, `Kerala`, `5`                 |
| **Variables**   | Unknowns                             | `x`, `y`, `z`                         |
| **Predicates**  | Describe relationships or properties | `Loves(John, Mary)`                   |
| **Functions**   | Map objects to objects               | `Mother(x)`                           |
| **Connectives** | Logical operators                    | ∧ (and), ∨ (or), → (implies), ¬ (not) |
| **Quantifiers** | Specify “how many”                   | ∀ (for all), ∃ (there exists)         |

---

### ✨ Example:

> “Every student is smart.”
> → ∀x [Student(x) → Smart(x)]

> “There exists a student who is smart.”
> → ∃x [Student(x) ∧ Smart(x)]

---

## 🌍 2️⃣ **Semantics of FOL (The Meaning)**

Semantics tells us **what the sentences *mean*** — i.e., when they’re true or false in the real world.

| Concept            | Explanation                                                                               |
| ------------------ | ----------------------------------------------------------------------------------------- |
| **Domain**         | The set of all possible objects we talk about (e.g., all students in a class).            |
| **Interpretation** | Assigns meaning to symbols — tells what each constant, predicate, and function refers to. |
| **Model**          | A specific interpretation that makes all sentences in the KB true.                        |

---

### 💡 Example of Meaning:

For sentence ∀x [Student(x) → Smart(x)]
If our **domain** = {Navi, Nim, Feb},
and the **interpretation** says
Student = {Navi, Nim, Feb}, Smart = {Navi, Nim},

→ Then this sentence is **false** (because Feb isn’t smart).

---

### 🧾 Summary:

> **Syntax of FOL** defines the structure and symbols used to represent knowledge, while
> **Semantics of FOL** defines how those symbols get meaning in a real-world model.
> Together, they let AI represent complex relationships between objects using quantifiers, predicates, and logical connectives.

---


## 🧩 **1️⃣ Resolution in First Order Logic**

### 💡 Concept:

Just like propositional resolution, but here we must deal with **variables** and **quantifiers**.

> It’s used to prove that KB ⊨ α by showing KB ∧ ¬α is inconsistent (leads to contradiction).

---

### ⚙️ **Steps in FOL Resolution:**

1️⃣ **Convert sentences into CNF** (remove implications, push NOTs inward, standardize variables, Skolemize, etc.)
2️⃣ **Eliminate universal quantifiers** (assume all variables are universally quantified).
3️⃣ **Resolve** clauses that contain *complementary literals* (like P(x) and ¬P(y))
4️⃣ **Apply Unification** (to make variables match).
5️⃣ Repeat until either contradiction (∅) is found ✅ or no new clauses are produced ❌.

---

### 🧠 **Unification**

A key step unique to FOL — it makes two literals *identical* by substituting variables.
Example:

```
P(x, a) and P(b, y)
Unifier = {x/b, y/a}
```

---

### ✨ **Example**

Given:

1. ¬Human(x) ∨ Mortal(x)
2. Human(Socrates)

Goal: Prove Mortal(Socrates)

* Negate goal → ¬Mortal(Socrates)
* Resolve (1) and (2): substitute x = Socrates → Mortal(Socrates)
* Resolving Mortal(Socrates) with ¬Mortal(Socrates) → contradiction ✅

Hence, **Socrates is Mortal** proved.

---

## 🧩 **2️⃣ Forward Chaining**

### 💡 Idea:

Start from known **facts** and **apply rules** to infer new facts — **data-driven reasoning**.

> Example Rule: If A → B, and A is true, infer B.

---

### ⚙️ **Algorithm Steps**

1️⃣ Start with all facts in the KB.
2️⃣ Find rules where the premises (IF part) are satisfied by known facts.
3️⃣ Add the conclusion (THEN part) to the KB.
4️⃣ Repeat until the goal is found or no new facts appear.

---

### 🧠 **Example**

Rules:

1. Human(x) → Mortal(x)
   Fact: Human(Socrates)

Then by forward chaining → Mortal(Socrates) ✅

---

## 🧩 **3️⃣ Backward Chaining**

### 💡 Idea:

Start from the **goal** and work *backward* — **goal-driven reasoning**.

> “To prove B, what facts or rules do I need?”

---

### ⚙️ **Algorithm Steps**

1️⃣ Start with the goal (query).
2️⃣ Find a rule whose **conclusion** matches the goal.
3️⃣ Make the rule’s **premises** new subgoals.
4️⃣ Prove those subgoals recursively from facts or other rules.
5️⃣ If all subgoals are true → goal proven ✅

---

### 🧠 **Example**

Goal: Mortal(Socrates)

Rule: Human(x) → Mortal(x)
Subgoal: Human(Socrates)

Fact: Human(Socrates) ✅
→ So Mortal(Socrates) is proved.

---

## 🏁 **Summary Table**

| Method                | Direction         | Type        | When Used             | Example Use       |
| --------------------- | ----------------- | ----------- | --------------------- | ----------------- |
| **Resolution**        | Bidirectional     | Rule-based  | Theorem proving       | Logical deduction |
| **Forward Chaining**  | From facts → goal | Data-driven | When many facts known | Expert systems    |
| **Backward Chaining** | From goal → facts | Goal-driven | When few goals        | Prolog queries    |

---
