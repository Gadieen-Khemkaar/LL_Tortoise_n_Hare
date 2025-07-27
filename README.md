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
### 🎯 Find the Starting Point of a Loop in a Linked List

After detecting a loop using Floyd’s Cycle Detection Algorithm, we can find the node where the loop starts.

#### 🔁 How It Works:
- Detect the meeting point of slow and fast.
- Move one pointer to the head.
- Move both pointers one step at a time.
- They will meet at the **starting node of the loop**.

#### ✅ Code (C++):
```cpp
ListNode* detectCycle(ListNode *head) {
    ListNode *slow = head, *fast = head;

    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;

        if (slow == fast) {
            fast = head;
            while (slow != fast) {
                slow = slow->next;
                fast = fast->next;
            }
            return slow;
        }
    }

    return NULL;
}
---
 🔓 Removing Loop in Linked List

Once a cycle is detected, we can remove it by:

1. Finding the start of the loop using Floyd’s Algorithm.
2. Traversing the loop to find the node that links back to the start.
3. Breaking the cycle by setting `loopNode->next = NULL`.

#### ✂️ Sample Code in C++:
```cpp
void removeLoop(ListNode* head) {
    ListNode* slow = head;
    ListNode* fast = head;

    // Detect loop
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) break;
    }

    if (slow != fast) return;

    fast = head;

    if (slow == fast) {
        while (slow->next != fast)
            slow = slow->next;
        slow->next = NULL;
        return;
    }

    while (slow->next != fast->next) {
        slow = slow->next;
        fast = fast->next;
    }

    slow->next = NULL;
}
