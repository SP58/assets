---
title: Insert into a Binary Search Tree
summary: Insert into a Binary Search Tree - Solution Explained
url: "/posts/insert-into-a-binary-search-tree"
date: 2020-10-26T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Insert into a Binary Search Tree LeetCode Solution Explained in all languages", "701", "leetcode question 701", "Insert into a Binary Search Tree", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/insert-into-a-binary-search-tree.webp
    alt: Insert into a Binary Search Tree - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [701. Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree)


## Description

<p>You are given the <code>root</code> node of a binary search tree (BST) and a <code>value</code> to insert into the tree. Return <em>the root node of the BST after the insertion</em>. It is <strong>guaranteed</strong> that the new value does not exist in the original BST.</p>

<p><strong>Notice</strong>&nbsp;that there may exist&nbsp;multiple valid ways for the&nbsp;insertion, as long as the tree remains a BST after insertion. You can return <strong>any of them</strong>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0701.Insert%20into%20a%20Binary%20Search%20Tree/images/insertbst.jpg" style="width: 752px; height: 221px;" />
<pre>
<strong>Input:</strong> root = [4,2,7,1,3], val = 5
<strong>Output:</strong> [4,2,7,1,3,5]
<strong>Explanation:</strong> Another accepted tree is:
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0701.Insert%20into%20a%20Binary%20Search%20Tree/images/bst.jpg" style="width: 352px; height: 301px;" />
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [40,20,60,10,30,50,70], val = 25
<strong>Output:</strong> [40,20,60,10,30,50,70,null,null,25]
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> root = [4,2,7,1,3,null,null,null,null,null,null], val = 5
<strong>Output:</strong> [4,2,7,1,3,5]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in&nbsp;the tree will be in the range <code>[0,&nbsp;10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>8</sup> &lt;= Node.val &lt;= 10<sup>8</sup></code></li>
	<li>All the values <code>Node.val</code> are <strong>unique</strong>.</li>
	<li><code>-10<sup>8</sup> &lt;= val &lt;= 10<sup>8</sup></code></li>
	<li>It&#39;s <strong>guaranteed</strong> that <code>val</code> does not exist in the original BST.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def insertIntoBST(self, root: TreeNode, val: int) -> TreeNode:
        def dfs(root):
            if root is None:
                return TreeNode(val)
            if root.val < val:
                root.right = dfs(root.right)
            else:
                root.left = dfs(root.left)
            return root

        return dfs(root)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    public TreeNode insertIntoBST(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }
        if (root.val < val) {
            root.right = insertIntoBST(root.right, val);
        } else {
            root.left = insertIntoBST(root.left, val);
        }
        return root;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        if (!root) return new TreeNode(val);
        if (root->val < val)
            root->right = insertIntoBST(root->right, val);
        else
            root->left = insertIntoBST(root->left, val);
        return root;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func insertIntoBST(root *TreeNode, val int) *TreeNode {
	if root == nil {
		return &TreeNode{Val: val}
	}
	if root.Val < val {
		root.Right = insertIntoBST(root.Right, val)
	} else {
		root.Left = insertIntoBST(root.Left, val)
	}
	return root
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
