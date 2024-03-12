---
title: Maximum Depth of N-ary Tree
summary: Maximum Depth of N-ary Tree - Solution Explained
url: "/posts/maximum-depth-of-n-ary-tree"
date: 2020-11-01T17:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Maximum Depth of N-ary Tree LeetCode Solution Explained in all languages", "559", "leetcode question 559", "Maximum Depth of N-ary Tree", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/maximum-depth-of-n-ary-tree.webp
    alt: Maximum Depth of N-ary Tree - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [559. Maximum Depth of N-ary Tree](https://leetcode.com/problems/maximum-depth-of-n-ary-tree)


## Description

<p>Given a n-ary tree, find its maximum depth.</p>

<p>The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.</p>

<p><em>Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<p><img src="https://spcdn.pages.dev/leetcode/problems/0559.Maximum%20Depth%20of%20N-ary%20Tree/images/narytreeexample.png" style="width: 100%; max-width: 300px;" /></p>

<pre>
<strong>Input:</strong> root = [1,null,3,2,4,null,5,6]
<strong>Output:</strong> 3
</pre>

<p><strong class="example">Example 2:</strong></p>

<p><img alt="" src="https://spcdn.pages.dev/leetcode/problems/0559.Maximum%20Depth%20of%20N-ary%20Tree/images/sample_4_964.png" style="width: 296px; height: 241px;" /></p>

<pre>
<strong>Input:</strong> root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
<strong>Output:</strong> 5
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The total number of nodes is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li>The depth of the n-ary tree is less than or equal to <code>1000</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""


class Solution:
    def maxDepth(self, root: 'Node') -> int:
        if root is None:
            return 0
        return 1 + max([self.maxDepth(child) for child in root.children], default=0)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> children;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, List<Node> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
    public int maxDepth(Node root) {
        if (root == null) {
            return 0;
        }
        int ans = 1;
        for (Node child : root.children) {
            ans = Math.max(ans, 1 + maxDepth(child));
        }
        return ans;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val) {
        val = _val;
    }

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
public:
    int maxDepth(Node* root) {
        if (!root) return 0;
        int ans = 1;
        for (auto& child : root->children) ans = max(ans, 1 + maxDepth(child));
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
/**
 * Definition for a Node.
 * type Node struct {
 *     Val int
 *     Children []*Node
 * }
 */

func maxDepth(root *Node) int {
	if root == nil {
		return 0
	}
	ans := 1
	for _, child := range root.Children {
		ans = max(ans, 1+maxDepth(child))
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
