## 🧠 1️⃣ Problem-Solving Agents

A **problem-solving agent** is a type of **goal-based agent** — it doesn’t just react; it *plans*.

👉 It works like this:

1. **Define the goal** (what we want to achieve)
2. **Formulate the problem** (how to reach that goal)
3. **Search for a solution**
4. **Execute** the best sequence of actions

🌀 **Example:**
A robot vacuum (Roomba) →
Goal: clean the entire floor
Problem: find a path to cover all dirty spots
Solution: search for a path without missing areas or getting stuck

---

## 🧩 2️⃣ Example Problems

AI problems often use small puzzles to test search strategies.

| Problem                      | Goal                   | Example            |
| ---------------------------- | ---------------------- | ------------------ |
| **8-puzzle**                 | Arrange tiles in order | Heuristic search   |
| **Route finding**            | Find shortest path     | GPS navigation     |
| **Missionaries & Cannibals** | Safe crossing puzzle   | Constraint search  |
| **Chess**                    | Checkmate opponent     | Adversarial search |

---

## 🔍 3️⃣ Searching for Solutions

Search = systematically exploring possible **states** to find a **path** from start → goal.

We represent a problem as a **state space**:

* **Initial state**: where we start
* **Actions**: what moves we can make
* **Transition model**: what happens after an action
* **Goal test**: checks if goal reached
* **Path cost**: total cost (distance, time, etc.)

---

Now, search strategies come in ✨two major types✨:

| Type                  | Description                 | Example            |
| --------------------- | --------------------------- | ------------------ |
| **Uninformed search** | No extra info — brute-force | BFS, DFS, DLS, IDS |
| **Informed search**   | Uses heuristic to guide     | Greedy, A*         |


