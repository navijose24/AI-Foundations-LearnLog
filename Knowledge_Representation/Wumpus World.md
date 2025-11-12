### 🧩 **What is Wumpus World?**

It’s a *logical environment* used to test how an AI agent can **use knowledge and reasoning** to survive and achieve goals.

---

### 🌍 **The Environment:**

* The world is a **grid of rooms (4×4)**.
* The agent starts at the **bottom-left** corner.
* Each room may contain:

  * 🧌 **Wumpus:** a monster that eats the agent.
  * ⚫ **Pit:** a deadly hole — if the agent falls, it dies.
  * 💰 **Gold:** the treasure to collect.
  * 💨 **Breeze:** felt in squares next to a pit.
  * 💀 **Stench:** smelled in squares next to the Wumpus.

---

### 🎯 **Goal of the Agent:**

✅ Collect the gold
✅ Avoid the pits and the Wumpus
✅ Exit safely

---

### 🧠 **How the Agent Thinks:**

The agent uses its **Knowledge Base (KB)** and *logical inference* to decide safe moves.

Example:

* If it **feels Breeze** → there’s a pit nearby.
* If it **smells Stench** → Wumpus is in one of the neighboring squares.
* If there’s *no Breeze or Stench* → all nearby rooms are safe.

So it keeps *TELL*-ing the KB what it perceives, *ASK*-ing which rooms are safe, and then *moves* logically.

---


## 🧩 **How the Wumpus Agent Uses Logic**

### 🌿 1️⃣ The Idea

The agent can’t *see* the whole cave — it only senses clues (like breeze or stench) in each room.
So it must use **logical reasoning** to *infer* where the Wumpus or pits might be.

The agent stores all this info in its **Knowledge Base (KB)** — using **propositional logic statements**.

---

### 🌿 2️⃣ Propositional Logic Representation

Each fact is written as a **propositional symbol**:

* `B(x,y)` → there’s a Breeze in cell (x,y)
* `P(x,y)` → there’s a Pit in cell (x,y)
* `S(x,y)` → there’s a Stench in cell (x,y)
* `W(x,y)` → Wumpus is in cell (x,y)
* `OK(x,y)` → cell (x,y) is safe

---

### 🌿 3️⃣ Example of Logical Rules

**Rule 1: Breeze Rule**

> If there’s a Breeze in a cell, there must be at least one Pit in an adjacent cell.
> 👉 `B(x,y) ⇔ [P(x-1,y) ∨ P(x+1,y) ∨ P(x,y-1) ∨ P(x,y+1)]`

**Rule 2: No Breeze Rule**

> If there’s no Breeze, then *no adjacent cell* contains a Pit.
> 👉 `¬B(x,y) ⇒ [¬P(x-1,y) ∧ ¬P(x+1,y) ∧ ¬P(x,y-1) ∧ ¬P(x,y+1)]`

**Rule 3: Stench Rule**

> If there’s a Stench in a cell, the Wumpus is in one of the neighboring cells.
> 👉 `S(x,y) ⇔ [W(x-1,y) ∨ W(x+1,y) ∨ W(x,y-1) ∨ W(x,y+1)]`

---

### 🌿 4️⃣ Reasoning Example (step-by-step)

The agent starts at (1,1):

* Percepts: **No Breeze**, **No Stench**
  ⇒ So all adjacent rooms (1,2) and (2,1) are **safe** ✅

It moves to (2,1):

* Percept: **Breeze**
  ⇒ There’s a pit in one of (1,1), (3,1), (2,2)
  But (1,1) is safe ⇒ so the pit must be in (2,2). 💡

So it marks (2,2) as *dangerous*, avoids it, and continues exploring safely.

---

### 🌿 5️⃣ Key takeaway

The agent combines:

* **TELL** (store percepts as logic statements)
* **ASK** (use inference to find safe cells)
* **Action** (move safely / grab gold / shoot Wumpus)

---

✅ **Summary **

> In Wumpus World, the knowledge-based agent uses propositional logic to infer safe and dangerous rooms. Logical rules map percepts like breeze or stench to possible pit or Wumpus locations, allowing the agent to plan actions safely.

---

