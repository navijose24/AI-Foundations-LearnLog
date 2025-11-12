## 🎮 **1️⃣ Adversarial Search**

### 💡 What it means

* Adversarial search is used in **competitive environments** (like games).
* Here, **two or more agents** act against each other.
* One player’s gain = another player’s loss → a **zero-sum game**.

🧩 **Examples:** Chess, Tic-Tac-Toe, Checkers.

---

### 🧠 **Game Representation**

A game can be represented as a **state-space tree**:

* **Nodes:** represent possible states of the game (positions on the board).
* **Edges:** represent player moves.
* **Levels alternate** between players (MAX and MIN).

| Player  | Role                                   |
| ------- | -------------------------------------- |
| **MAX** | Tries to maximize the score (AI)       |
| **MIN** | Tries to minimize the score (Opponent) |

---

### 🧩 **Optimal Decisions in Games**

Each player assumes the opponent plays **optimally**.
That means:

* MAX chooses moves that **maximize** its minimum guaranteed score.
* MIN chooses moves that **minimize** MAX’s maximum gain.

This leads to the **Minimax Algorithm** 👇

---

## ⚙️ **Minimax Algorithm**

It is used to determine the **best move** for MAX, assuming MIN plays perfectly.

---

### 🧩 **Alpha–Beta Pruning**

To speed things up, we **skip branches** that can’t affect the final result.
We’ll cover this next (after you confirm you’re comfy with Minimax).

---
