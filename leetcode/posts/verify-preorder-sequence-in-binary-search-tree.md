---
title: Verify Preorder Sequence in Binary Search Tree
summary: Verify Preorder Sequence in Binary Search Tree - Solution Explained
url: "/posts/verify-preorder-sequence-in-binary-search-tree"
date: 2020-11-14T09:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Verify Preorder Sequence in Binary Search Tree LeetCode Solution Explained in all languages", "255", "leetcode question 255", "Verify Preorder Sequence in Binary Search Tree", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/verify-preorder-sequence-in-binary-search-tree.webp
    alt: Verify Preorder Sequence in Binary Search Tree - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [255. Verify Preorder Sequence in Binary Search Tree](https://leetcode.com/problems/verify-preorder-sequence-in-binary-search-tree)


## Description

<p>Given an array of <strong>unique</strong> integers <code>preorder</code>, return <code>true</code> <em>if it is the correct preorder traversal sequence of a binary search tree</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0255.Verify%20Preorder%20Sequence%20in%20Binary%20Search%20Tree/images/preorder-tree.jpg" style="width: 292px; height: 302px;" />
<pre>
<strong>Input:</strong> preorder = [5,2,1,3,6]
<strong>Output:</strong> true
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> preorder = [5,2,6,1,3]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= preorder.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= preorder[i] &lt;= 10<sup>4</sup></code></li>
	<li>All the elements of <code>preorder</code> are <strong>unique</strong>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you do it using only constant space complexity?</p>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def verifyPreorder(self, preorder: List[int]) -> bool:
        stk = []
        last = -inf
        for x in preorder:
            if x < last:
                return False
            while stk and stk[-1] < x:
                last = stk.pop()
            stk.append(x)
        return True
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean verifyPreorder(int[] preorder) {
        Deque<Integer> stk = new ArrayDeque<>();
        int last = Integer.MIN_VALUE;
        for (int x : preorder) {
            if (x < last) {
                return false;
            }
            while (!stk.isEmpty() && stk.peek() < x) {
                last = stk.poll();
            }
            stk.push(x);
        }
        return true;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool verifyPreorder(vector<int>& preorder) {
        stack<int> stk;
        int last = INT_MIN;
        for (int x : preorder) {
            if (x < last) return false;
            while (!stk.empty() && stk.top() < x) {
                last = stk.top();
                stk.pop();
            }
            stk.push(x);
        }
        return true;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func verifyPreorder(preorder []int) bool {
	var stk []int
	last := math.MinInt32
	for _, x := range preorder {
		if x < last {
			return false
		}
		for len(stk) > 0 && stk[len(stk)-1] < x {
			last = stk[len(stk)-1]
			stk = stk[0 : len(stk)-1]
		}
		stk = append(stk, x)
	}
	return true
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
