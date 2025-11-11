###  **Concept: Alpha–Beta Pruning**


> Alpha–Beta Pruning is an optimized version of the Minimax algorithm.
  It eliminates branches that will not affect the final decision, reducing the number of nodes explored — while giving the same result as Minimax.


* It’s an **optimization** for the **Minimax algorithm**.
* Idea: Don’t waste time exploring moves that **won’t affect the final decision**.

In Minimax, we check all possible moves (the whole game tree).
Alpha–Beta Pruning **cuts off branches** that can’t influence the outcome — like ignoring bad options once we know something better exists.

* **Alpha (α):** Best (highest) value found so far for the *MAX* player.
* **Beta (β):** Best (lowest) value found so far for the *MIN* player.

⏩ When **β ≤ α**, we stop exploring that branch — it’s useless.


---


**Pseudocode**

def alphabeta(node, depth, α, β, maximizingPlayer):
    if node is terminal or depth == 0:
        return value(node)

    if maximizingPlayer:
        value = -∞
        for child in node.children:
            value = max(value, alphabeta(child, depth-1, α, β, False))
            α = max(α, value)
            if β <= α:
                break   # β cut-off
        return value

    else:  # Minimizing player
        value = +∞
        for child in node.children:
            value = min(value, alphabeta(child, depth-1, α, β, True))
            β = min(β, value)
            if β <= α:
                break   # α cut-off
        return value


---

### 🌳 **Example Tree:**

Let’s imagine a simple game tree:

```
         A (MAX)
       /         \
   B(MIN)        C(MIN)
  /   \          /   \
3     5        6     9
```

#### Step 1:

MAX starts at A → tries both B and C.

#### Step 2 (B node):

B is MIN → picks min(3, 5) = **3**
→ So A’s left branch gives **3**

#### Step 3 (C node):

C is MIN → picks min(6, 9) = **6**

#### Step 4 (A node):

A (MAX) picks max(3, 6) = **6**

So the **best move for MAX** = value **6** (go right toward C).

---

### 💡 **Now with Pruning**

If while exploring C’s left child (value = 6),
we already know **B gave 3**,
and C’s next child gives a value ≥ 6,
then for MIN, that’s **worse** — it’ll never pick it.
So we **prune** (skip) the rest of C’s branch.

Thus, Alpha–Beta saves computation without changing the result!

---


### 🧠 **Game Tree Example**

```
                 A (MAX)
               /         \
         B (MIN)           C (MIN)
        /      \           /      \
     D(MAX)   E(MAX)    F(MAX)   G(MAX)
     / \       / \       / \       / \
    3  5     6  9     1  2     0  7
```

We’ll trace α and β updates as we move.

---

### 🔹 **Step 1: Start**

At root **A (MAX)**:

* α = −∞, β = +∞

---

### 🔹 **Step 2: Explore left branch (B – MIN node)**

At B: α = −∞, β = +∞

Explore B’s first child → D (MAX)

* D’s children are 3 and 5 → D chooses **max(3,5)=5**
  → Value(D)=5

At B (MIN), β = min(+∞,5) = 5

Now explore B’s next child → E (MAX)

* E’s children: 6 and 9 → max(6,9)=9
  → Value(E)=9

At B: β = min(5,9)=**5**
✅ So B = 5

At A: α = max(−∞,5)=**5**

---

### 🔹 **Step 3: Explore right branch (C – MIN node)**

At C: α = 5, β = +∞

Explore C’s first child → F (MAX)

* F’s children: 1, 2 → max(1,2)=2
  → Value(F)=2

At C: β = min(+∞,2)=2

👉 Now note: β (2) ≤ α (5) → **PRUNE!**

No need to explore G (MAX), because MIN will never allow a value greater than 2 when MAX already has a 5 from left branch.

⛔ So, branch **G** is pruned.

---

### ✅ **Final Values**

* B = 5
* C = 2 (G skipped)
* A = max(5,2)=**5**

So the **best move for MAX** = Left branch (value 5).
And the **pruned branch saved time** (G skipped).

---

### ✨ **Summary**

| Symbol              | Meaning                                                    |
| ------------------- | ---------------------------------------------------------- |
| **α (Alpha)**       | Best value for MAX so far (lower bound)                    |
| **β (Beta)**        | Best value for MIN so far (upper bound)                    |
| **Prune condition** | When β ≤ α                                                 |
| **Purpose**         | Skip exploring branches that can’t affect the final result |

---

### 🧩 **Advantages**

✅ Same optimal result as Minimax
✅ Much faster (fewer nodes expanded)
✅ Works best when good moves are explored first

---


