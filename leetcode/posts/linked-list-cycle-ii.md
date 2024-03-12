---
title: Linked List Cycle II
summary: Linked List Cycle II - Solution Explained
url: "/posts/linked-list-cycle-ii"
date: 2020-11-19T02:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Linked List Cycle II LeetCode Solution Explained in all languages", "142", "leetcode question 142", "Linked List Cycle II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/linked-list-cycle-ii.webp
    alt: Linked List Cycle II - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii)


## Description

<p>Given the <code>head</code> of a linked list, return <em>the node where the cycle begins. If there is no cycle, return </em><code>null</code>.</p>

<p>There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the <code>next</code> pointer. Internally, <code>pos</code> is used to denote the index of the node that tail&#39;s <code>next</code> pointer is connected to (<strong>0-indexed</strong>). It is <code>-1</code> if there is no cycle. <strong>Note that</strong> <code>pos</code> <strong>is not passed as a parameter</strong>.</p>

<p><strong>Do not modify</strong> the linked list.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0142.Linked%20List%20Cycle%20II/images/circularlinkedlist.png" style="height: 145px; width: 450px;" />
<pre>
<strong>Input:</strong> head = [3,2,0,-4], pos = 1
<strong>Output:</strong> tail connects to node index 1
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the second node.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0142.Linked%20List%20Cycle%20II/images/circularlinkedlist_test2.png" style="height: 105px; width: 201px;" />
<pre>
<strong>Input:</strong> head = [1,2], pos = 0
<strong>Output:</strong> tail connects to node index 0
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the first node.
</pre>

<p><strong class="example">Example 3:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0142.Linked%20List%20Cycle%20II/images/circularlinkedlist_test3.png" style="height: 65px; width: 65px;" />
<pre>
<strong>Input:</strong> head = [1], pos = -1
<strong>Output:</strong> no cycle
<strong>Explanation:</strong> There is no cycle in the linked list.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of the nodes in the list is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>5</sup> &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
	<li><code>pos</code> is <code>-1</code> or a <strong>valid index</strong> in the linked-list.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Can you solve it using <code>O(1)</code> (i.e. constant) memory?</p>

## Solutions

### Solution 1: Two Pointers

We first use the fast and slow pointers to judge whether the linked list has a ring. If there is a ring, the fast and slow pointers will definitely meet, and the meeting node must be in the ring.

If there is no ring, the fast pointer will reach the tail of the linked list first, and return `null` directly.

If there is a ring, we then define an answer pointer $ans$ to point to the head of the linked list, and then let $ans$ and the slow pointer move forward together, moving one step at a time, until $ans$ and the slow pointer meet, and the meeting node is the ring entrance node.

Why can this find the entrance node of the ring?

Let's assume that the distance from the head node of the linked list to the entrance of the ring is $x$, the distance from the entrance of the ring to the meeting node is $y$, and the distance from the meeting node to the entrance of the ring is $z$. Then the distance traveled by the slow pointer is $x + y$, and the distance traveled by the fast pointer is $x + y + k \times (y + z)$, where $k$ is the number of times the fast pointer goes around the ring.

<p><img src="https://spcdn.pages.dev/leetcode/problems/0142.Linked%20List%20Cycle%20II/images/linked-list-cycle-ii.png" /></p>

Because the speed of the fast pointer is twice that of the slow pointer, it is $2 \times (x + y) = x + y + k \times (y + z)$, which can be deduced that $x + y = k \times (y + z)$, that is $x = (k - 1) \times (y + z) + z$.

That is to say, if we define an answer pointer $ans$ to point to the head of the linked list, and the $ans$ and the slow pointer move forward together, they will definitely meet at the ring entrance.

The time complexity is $O(n)$, where $n$ is the number of nodes in the linked list. The space complexity is $O(1)$.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        fast = slow = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                ans = head
                while ans != slow:
                    ans = ans.next
                    slow = slow.next
                return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head, slow = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                ListNode ans = head;
                while (ans != slow) {
                    ans = ans.next;
                    slow = slow.next;
                }
                return ans;
            }
        }
        return null;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* detectCycle(ListNode* head) {
        ListNode* fast = head;
        ListNode* slow = head;
        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
            if (slow == fast) {
                ListNode* ans = head;
                while (ans != slow) {
                    ans = ans->next;
                    slow = slow->next;
                }
                return ans;
            }
        }
        return nullptr;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func detectCycle(head *ListNode) *ListNode {
	fast, slow := head, head
	for fast != nil && fast.Next != nil {
		slow = slow.Next
		fast = fast.Next.Next
		if slow == fast {
			ans := head
			for ans != slow {
				ans = ans.Next
				slow = slow.Next
			}
			return ans
		}
	}
	return nil
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     val: number
 *     next: ListNode | null
 *     constructor(val?: number, next?: ListNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.next = (next===undefined ? null : next)
 *     }
 * }
 */

function detectCycle(head: ListNode | null): ListNode | null {
    let [slow, fast] = [head, head];
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow === fast) {
            let ans = head;
            while (ans !== slow) {
                ans = ans.next;
                slow = slow.next;
            }
            return ans;
        }
    }
    return null;
}
```
{{< /terminal >}}

{{< terminal title="JavaScript Code" >}}
```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var detectCycle = function (head) {
    let [slow, fast] = [head, head];
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow === fast) {
            let ans = head;
            while (ans !== slow) {
                ans = ans.next;
                slow = slow.next;
            }
            return ans;
        }
    }
    return null;
};
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
