---
title: Verify Preorder Serialization of a Binary Tree
summary: Verify Preorder Serialization of a Binary Tree - Solution Explained
url: "/posts/verify-preorder-serialization-of-a-binary-tree"
date: 2020-11-11T05:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Verify Preorder Serialization of a Binary Tree LeetCode Solution Explained in all languages", "331", "leetcode question 331", "Verify Preorder Serialization of a Binary Tree", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/verify-preorder-serialization-of-a-binary-tree.webp
    alt: Verify Preorder Serialization of a Binary Tree - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [331. Verify Preorder Serialization of a Binary Tree](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree)


## Description

<p>One way to serialize a binary tree is to use <strong>preorder traversal</strong>. When we encounter a non-null node, we record the node&#39;s value. If it is a null node, we record using a sentinel value such as <code>&#39;#&#39;</code>.</p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0331.Verify%20Preorder%20Serialization%20of%20a%20Binary%20Tree/images/pre-tree.jpg" style="width: 362px; height: 293px;" />
<p>For example, the above binary tree can be serialized to the string <code>&quot;9,3,4,#,#,1,#,#,2,#,6,#,#&quot;</code>, where <code>&#39;#&#39;</code> represents a null node.</p>

<p>Given a string of comma-separated values <code>preorder</code>, return <code>true</code> if it is a correct preorder traversal serialization of a binary tree.</p>

<p>It is <strong>guaranteed</strong> that each comma-separated value in the string must be either an integer or a character <code>&#39;#&#39;</code> representing null pointer.</p>

<p>You may assume that the input format is always valid.</p>

<ul>
	<li>For example, it could never contain two consecutive commas, such as <code>&quot;1,,3&quot;</code>.</li>
</ul>

<p><strong>Note:&nbsp;</strong>You are not allowed to reconstruct the tree.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> preorder = "9,3,4,#,#,1,#,#,2,#,6,#,#"
<strong>Output:</strong> true
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> preorder = "1,#"
<strong>Output:</strong> false
</pre><p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> preorder = "9,#,#,1"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= preorder.length &lt;= 10<sup>4</sup></code></li>
	<li><code>preorder</code> consist of integers in the range <code>[0, 100]</code> and <code>&#39;#&#39;</code> separated by commas <code>&#39;,&#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def isValidSerialization(self, preorder: str) -> bool:
        stk = []
        for c in preorder.split(","):
            stk.append(c)
            while len(stk) > 2 and stk[-1] == stk[-2] == "#" and stk[-3] != "#":
                stk = stk[:-3]
                stk.append("#")
        return len(stk) == 1 and stk[0] == "#"
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean isValidSerialization(String preorder) {
        String[] strs = preorder.split(",");
        int diff = 1;
        for (String s : strs) {
            if (--diff < 0) {
                return false;
            }
            if (!s.equals("#")) {
                diff += 2;
            }
        }
        return diff == 0;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool isValidSerialization(string preorder) {
        vector<string> stk;
        stringstream ss(preorder);
        string s;
        while (getline(ss, s, ',')) {
            stk.push_back(s);
            while (stk.size() >= 3 && stk[stk.size() - 1] == "#" && stk[stk.size() - 2] == "#" && stk[stk.size() - 3] != "#") {
                stk.pop_back();
                stk.pop_back();
                stk.pop_back();
                stk.push_back("#");
            }
        }
        return stk.size() == 1 && stk[0] == "#";
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func isValidSerialization(preorder string) bool {
	stk := []string{}
	for _, s := range strings.Split(preorder, ",") {
		stk = append(stk, s)
		for len(stk) >= 3 && stk[len(stk)-1] == "#" && stk[len(stk)-2] == "#" && stk[len(stk)-3] != "#" {
			stk = stk[:len(stk)-3]
			stk = append(stk, "#")
		}
	}
	return len(stk) == 1 && stk[0] == "#"
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean isValidSerialization(String preorder) {
        List<String> stk = new ArrayList<>();
        for (String s : preorder.split(",")) {
            stk.add(s);
            while (stk.size() >= 3 && stk.get(stk.size() - 1).equals("#")
                && stk.get(stk.size() - 2).equals("#") && !stk.get(stk.size() - 3).equals("#")) {
                stk.remove(stk.size() - 1);
                stk.remove(stk.size() - 1);
                stk.remove(stk.size() - 1);
                stk.add("#");
            }
        }
        return stk.size() == 1 && stk.get(0).equals("#");
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
