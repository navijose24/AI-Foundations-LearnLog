###  **Logical Agents — Knowledge-Based Agents**

#### 🧠 What it means:

A **logical agent** is an AI that reasons and makes decisions **using knowledge and logic** rather than just pre-coded instructions.

#### 🧩 The Core Idea:

Unlike normal reflex agents (which react directly to inputs), a *knowledge-based agent* stores what it knows about the world and uses **inference** to figure out what to do next.

---

#### 💡 Structure of a Knowledge-Based Agent:

1. **Knowledge Base (KB)** – stores facts and rules (like “If it’s raining → carry an umbrella”)
2. **Inference Engine** – applies logical reasoning to the KB (derives new facts)
3. **Percept & Action Loop** – observes the world, updates KB, and decides actions.

---

#### ⚙️ Example:

Imagine a vacuum-cleaner robot:

* Perceives: “The current room is dirty.”
* KB says: “If a room is dirty → clean it.”
* The inference engine reasons: “Room1 is dirty → I should clean Room1.”
* Action: The robot cleans it ✅

---

#### 📘 Where it’s used:

* Expert systems (like medical diagnosis)
* Virtual assistants (reasoning over knowledge graphs)
* Game AIs and chatbots (for logical dialogue)
* Robotic planning and decision-making.

---

### Knowledge-Base

 > A Knowledge-Based Agent is an intelligent agent that uses logical reasoning over a knowledge base to decide its actions. The algorithm uses the TELL and ASK operations to update and query the knowledge base.


---

### 🧩 **Algorithm (in words + meaning)**

```text
function KB-Agent(percept) returns an action
    static: KB, a knowledge base
            t, a counter (time step, initially 0)
    TELL(KB, MAKE-PERCEPT-SENTENCE(percept, t))
    action ← ASK(KB, MAKE-ACTION-QUERY(t))
    TELL(KB, MAKE-ACTION-SENTENCE(action, t))
    t ← t + 1
    return action
```

---

### 🧠 **Concept Summary:**

* **TELL:** Add new facts.
* **ASK:** Query the KB to derive conclusions.
* **Action:** The agent’s decision based on logical reasoning.
* **KB-Agent** = *Think → Decide → Learn → Repeat.*

---

### 🪄 **Example (vacuum world):**

* Percept: “Room A is dirty.”
* TELL(KB, “Dirty(A)”)
* ASK(KB, “What should I do?”) → KB says “Clean(A)”
* TELL(KB, “Action=Clean(A)”)
* Executes “Clean(A)”

---
