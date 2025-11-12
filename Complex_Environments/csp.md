## 🧩 **1️⃣ Constraint Satisfaction Problem (CSP)**

    > “A Constraint Satisfaction Problem is a search problem where the goal is to assign values to variables satisfying all constraints. CSPs are represented by variables, domains, and constraints and solved using propagation and backtracking.”

### 💡 **Definition**

A **CSP** is a problem defined by:

* **Variables:** (X_1, X_2, ..., X_n)
* **Domains:** Possible values for each variable (D_1, D_2, ..., D_n)
* **Constraints:** Relations that restrict which combinations of values are allowed.

Goal → **Find a value for each variable** such that **all constraints are satisfied.**

---

### 🧠 **Example: Map Coloring Problem**

| Variable                 | Domain             | Constraint                   |
| ------------------------ | ------------------ | ---------------------------- |
| WA, NT, SA, Q, NSW, V, T | {Red, Green, Blue} | Adjacent states ≠ same color |

**Representation as graph:**

* Nodes → Regions (variables)
* Edges → “≠” constraints between neighboring regions

👉 Objective: assign colors to all nodes with no adjacent same color.

---

### 💬 **Other Examples**

* Sudoku → each row, column, box = unique numbers 1–9
* N-Queens → no two queens attack each other
* Scheduling → assign time slots to jobs with no overlap

---

### 🧠 **Why CSPs are Powerful**

Instead of brute-force search, CSPs use:

* **Constraint propagation** → reduce domains
* **Heuristics (MRV, LCV)** → smartly choose variables
* **Backtracking search** → systematically assign and undo

This combination makes solving large problems efficient and logical 🔥

---

## Types of Constraints in CSP

| **Type**   | **Acts On**                 | **Example**                  | **Effect**                    |
| ------ | ----------------------- | ------------------------ | ------------------------- |
| Unary  | One variable            | X ≠ Red                  | Reduces domain            |
| Binary | Two variables           | A ≠ B                    | Restricts pairwise values |
| Global | Three or more variables | AllDifferent(X1, X2, X3) | Large-scale restriction   |
