## ⚙️ **Minimax Algorithm**

It is used to determine the **best move** for MAX, assuming MIN plays perfectly.

### 🔹 Steps:

1. **Generate the entire game tree** up to terminal states (end of game).
2. **Assign utility values** to terminal nodes (win = +1, lose = −1, draw = 0).
3. **Propagate values upward**:

   * MAX node takes **maximum** of its children.
   * MIN node takes **minimum** of its children.
4. The value at the root = best outcome assuming optimal play.

---

### 🧩 Example

Imagine a small game tree:

```
           (A) MAX
         /        \
     (B) MIN     (C) MIN
     / \          / \
    3   5        2   9
```

* At (B), MIN chooses min(3,5) = **3**
* At (C), MIN chooses min(2,9) = **2**
* At (A), MAX chooses max(3,2) = **3**

✅ So MAX’s best move = Left branch (value 3).

---
