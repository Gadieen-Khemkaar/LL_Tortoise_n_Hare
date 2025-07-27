## 🔁 Loop Detection in Linked List — Tortoise and Hare Algorithm

### ✅ Problem Statement:

Given a singly linked list, **determine whether it contains a cycle (loop)**.

---

### 🧠 Concept:

We use **Floyd’s Cycle Detection Algorithm**, also known as the **Tortoise and Hare Algorithm**.

* **Tortoise (slow pointer):** moves one node at a time.
* **Hare (fast pointer):** moves two nodes at a time.

If there is a loop, the fast pointer will eventually "lap" and meet the slow pointer inside the loop.

---

### 🛠️ Algorithm Steps:

1. Initialize two pointers `slow` and `fast` at the head.
2. Move `slow` by one step and `fast` by two steps in each iteration.
3. If `slow == fast` at any point → **Cycle exists**.
4. If `fast` reaches the end (`NULL`) → **No cycle**.

---

### 💻 Code (C++):

```cpp
bool hasCycle(ListNode *head) {
    ListNode *slow = head;
    ListNode *fast = head;

    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;

        if (slow == fast) return true; // Cycle detected
    }

    return false; // No cycle
}
```

---

### ⏱️ Time and Space Complexity:

| Metric | Value           |
| ------ | --------------- |
| Time   | O(n)            |
| Space  | O(1) (constant) |

---

### 🔄 Bonus:

* ✅ **Detect if loop exists** ✔️
* 🎯 **Find the starting node of the loop** (can be added)
* ✂️ **Remove the loop** (can also be added)
