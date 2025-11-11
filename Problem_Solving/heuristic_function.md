## 🌟 **Heuristic Function (h(n))**

### 🔹 **Definition**

A **heuristic function** (h(n)) is an **estimate of the cost** (or distance) from a given node (n) to the goal state.
It is used in **informed search algorithms** (like A*, Greedy) to **guide** the search process toward the goal more efficiently.

> In short, a heuristic tells the algorithm *“how close am I to the goal?”*

---

### 🔹 **Purpose**

Without heuristics, the search explores blindly (like BFS or DFS).
With heuristics, the algorithm **chooses paths that look more promising**, reducing the number of nodes explored and speeding up the search.

---

### 🔹 **Notation**

For any node (n):

* (g(n)) → cost from the start node to (n).
* (h(n)) → estimated cost from (n) to the goal.
* (f(n) = g(n) + h(n)) → total estimated cost (used in A* search).

---

### 🔹 **Types of Heuristic Functions**

1. **Admissible Heuristic**

   * Never overestimates the true cost to reach the goal.
   * Ensures that A* search remains **optimal**.
     [
     h(n) \le h^*(n)
     ]
     where (h^*(n)) = true cost to reach goal from (n).

2. **Consistent (Monotonic) Heuristic**

   * Satisfies the triangle inequality:
     [
     h(n) \le c(n, n') + h(n')
     ]
     for every successor (n').
   * Guarantees **no re-expansions** in A* graph search.

---

### 🔹 **Examples (8-Puzzle Problem)**

1. **Misplaced Tile Heuristic (h₁)**

   * Counts the number of tiles not in their correct position.
   * Example:
     Start:

     ```
     2 8 3
     1 6 4
     7 _ 5
     ```

     Goal:

     ```
     1 2 3
     8 _ 4
     7 6 5
     ```

     → 4 tiles misplaced ⇒ h₁ = 4

2. **Manhattan Distance Heuristic (h₂)**

   * For each tile, count how many grid moves (up, down, left, right) away it is from its goal position.
   * Sum all these distances.
   * Example above ⇒ h₂ = 5

---

### 🔹 **Advantages of Using Heuristics**

✅ Reduces search time and memory.
✅ Finds optimal solutions faster (when admissible).
✅ Makes algorithms like A* practical for large problems.

---

### 🔹 **How to Derive Heuristics**

👉 From **relaxed problems** — remove one or more constraints to make it easier.
The cost of solving the relaxed problem gives an **admissible heuristic**.
Example:

* If tiles could move anywhere → Misplaced tile heuristic.
* If tiles move freely ignoring others → Manhattan distance heuristic.

---

### 🔹 **Comparison of Common Heuristics**

| Heuristic                   | How it works                     | Strength                  |
| --------------------------- | -------------------------------- | ------------------------- |
| **h₁ (Misplaced Tiles)**    | Counts misplaced tiles           | Simple but weak           |
| **h₂ (Manhattan Distance)** | Sum of distances                 | Stronger & admissible     |
| **Pattern Database**        | Stores optimal moves for subsets | Very strong, memory-heavy |

---

### 🧩 **Example in A***

If (g(n)=4), (h(n)=5)
→ (f(n)=g+h=9).
The node with the **lowest f(n)** is expanded first.

---

### 🏁 **Summary**

> A heuristic function h(n) provides an estimate of the cost from node n to the goal.
> It is used in informed search algorithms to guide exploration efficiently.
> A good heuristic is **admissible**, **consistent**, and **derived from a relaxed problem**.
> Common examples include the **misplaced tile** and **Manhattan distance** heuristics in the 8-puzzle problem.
> These improve search efficiency while maintaining optimality.

---
