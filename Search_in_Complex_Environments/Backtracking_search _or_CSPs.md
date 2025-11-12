###  Backtracking Search for CSPs

**Full form:** *Constraint Satisfaction Problems (CSPs)*

---

### 🧩 1. What it is:

Backtracking search is a **depth-first search algorithm** used to solve CSPs by **assigning values to variables one at a time** and **undoing (backtracking)** when a conflict is found.

---

### ⚙️ 2. Basic idea (steps):

1. Choose an unassigned variable.
2. Assign it a value that satisfies all current constraints.
3. If a violation occurs → **undo (backtrack)** and try another value.
4. Continue until all variables are assigned or no valid assignment exists.

---

### 🧠 3. Example:

**Problem:** 3-coloring a map (each region must have a different color than its neighbors).

* Assign Red to A → OK
* Assign Blue to B → OK
* Assign Red to C (neighbor of A)? ❌ conflict → backtrack → assign Green ✅

---

### ⚡ 4. Enhancements:

* **MRV (Minimum Remaining Values):** pick variable with fewest legal values first.
* **Degree heuristic:** choose variable involved in most constraints.
* **Forward checking:** eliminate invalid future values after each assignment.
* **Arc consistency (AC-3):** pre-filter inconsistent domains.

---


### 🎯 1. **MRV (Minimum Remaining Values heuristic)**

**Idea:** Choose the variable with the fewest legal values left in its domain.
**Why:** It detects dead ends early — fewer choices → higher constraint → resolve first.

**Algorithm (outline):**

```
function select_variable_MRV(variables):
    return variable v with smallest |Domain(v)|
```

✅ *Example:*
If A={1,2,3}, B={1}, C={1,2} → choose **B** (domain size = 1).

---

### 🔗 2. **Degree heuristic**

**Idea:** When MRV ties, choose the variable that participates in the **most constraints** with other unassigned variables.
**Why:** Helps reduce future conflicts faster.

**Algorithm (outline):**

```
function degree_heuristic(variables):
    return variable v with maximum number of constraints on unassigned vars
```

✅ *Example:*
If both A and B have 2 possible values, but A is linked to 4 others and B to 1 → pick **A**.

---

### 🔍 3. **Forward Checking**

**Idea:** After assigning a value to a variable, **remove inconsistent values** from neighboring variables’ domains.
**Why:** Prevents exploring paths that will later fail due to constraint violation.

**Algorithm:**

```
function forward_check(var, value, constraints):
    for each neighbor in neighbors(var):
        remove from Domain(neighbor) any value that conflicts with (var=value)
        if Domain(neighbor) becomes empty:
            return False  // inconsistency found
    return True
```

✅ *Example:*
If A=Red, and B cannot be Red (A–B connected), remove “Red” from B’s domain.

---

### 🧮 4. **Arc Consistency (AC-3 Algorithm)**

**Idea:** Enforce **local consistency** between every pair of variables (arcs).
Each variable’s values must have *some consistent support* in the connected variable’s domain.

**Algorithm (AC-3):**

```
function AC3(csp):
    queue = all arcs (Xi, Xj)
    while queue not empty:
        (Xi, Xj) = queue.pop()
        if revise(Xi, Xj):
            if Domain(Xi) empty:
                return False
            for each Xk in neighbors(Xi) - {Xj}:
                add (Xk, Xi) to queue
    return True

function revise(Xi, Xj):
    revised = False
    for each x in Domain(Xi):
        if no y in Domain(Xj) satisfies constraint(Xi, Xj):
            remove x from Domain(Xi)
            revised = True
    return revised
```

✅ *Example:*
If A=Red and B must differ from A, remove Red from B’s domain — repeat for all pairs.

---


### 🎯 **1. LCV – Least Constraining Value heuristic**

**Full form:** *Least Constraining Value*

**Idea:**
When assigning a value to a variable, choose the value that **rules out the fewest options** for the remaining unassigned variables.

**Goal:**
Keep future possibilities open → reduce the chance of backtracking later.

---

### ⚙️ **2. How it works (steps):**

```
function order_values_LCV(var, csp):
    for each value in Domain(var):
        count = number of values eliminated from neighbors if var=value
    sort values by count (ascending)
    return ordered values
```

✅ So — pick the value that eliminates the **least number** of options for others.

---

### 🌈 **3. Example (Map Coloring):**

Let’s say variable **A** can be {Red, Green, Blue}.
Neighbors: B, C

If:

* A=Red → removes Red from B and C (2 removals)
* A=Green → removes Green from B only (1 removal)
* A=Blue → removes Blue from B and C (2 removals)

Then **LCV = Green** (because it removes the fewest).

---

### 🧩 **4. Summary:**

| Heuristic | Decides                                | Strategy                             |
| --------- | -------------------------------------- | ------------------------------------ |
| **MRV**   | Which variable to assign next          | Choose the most constrained variable |
| **LCV**   | Which value to assign to that variable | Choose the least constraining value  |

---
