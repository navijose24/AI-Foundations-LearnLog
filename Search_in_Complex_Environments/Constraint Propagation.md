### 🎯 **1. What is Constraint Propagation?**

Constraint propagation is the process of **reducing variable domains** by using constraints to **eliminate inconsistent values**, spreading (propagating) the effects of each assignment throughout the network.

It ensures that **each variable’s domain only contains values consistent** with other variables’ constraints — *before* full search or during it.

---

### 🧩 **2. Why it matters:**

It helps detect conflicts **early**, reducing backtracking.
Instead of guessing values and failing later, it *shrinks domains progressively*.

---

### ⚙️ **3. How it works (general idea):**

1. When a variable gets a value or loses domain values,
2. Re-check all related constraints,
3. Remove inconsistent values from other connected variables,
4. Repeat this “propagation” until no more domains change.

---

### 🔄 **4. Algorithm (AC-3: most common for constraint propagation)**

This is how propagation is implemented efficiently:

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

**Meaning:**

* If a value in `Xi` has **no supporting value** in `Xj`, it’s removed.
* This “propagates” — removing one value can trigger more removals in connected variables.

---

### 🌼 **5. Example:**

Suppose we have variables:

* A = {1,2,3},
* B = {1,2},
  and constraint A < B

Then propagation removes:

* A=3 ❌ (no value in B is >3)
* A={1,2}, B={2} ✅

This pruning continues until all variables’ domains are consistent.

---
