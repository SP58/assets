---
title: Is Array a Preorder of Some ‌Binary Tree
summary: Is Array a Preorder of Some ‌Binary Tree - Solution Explained
url: "/posts/is-array-a-preorder-of-some-binary-tree"
date: 2020-08-01T20:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Is Array a Preorder of Some ‌Binary Tree LeetCode Solution Explained in all languages", "2764", "leetcode question 2764", "Is Array a Preorder of Some ‌Binary Tree", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/is-array-a-preorder-of-some-binary-tree.webp
    alt: Is Array a Preorder of Some ‌Binary Tree - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2764. Is Array a Preorder of Some ‌Binary Tree](https://leetcode.com/problems/is-array-a-preorder-of-some-binary-tree)


## Description

<p>Given a <strong>0-indexed</strong> integer <strong>2D array</strong> <code>nodes</code>, your task is to determine if the given array represents the <strong>preorder</strong> traversal of some <strong>binary</strong> tree.</p>

<p>For each index <code>i</code>, <code>nodes[i] = [id, parentId]</code>, where <code>id</code> is the id of the node at the index <code>i</code> and <code>parentId</code> is the id of its parent in the tree (if the node has no parent, then <code>parentId == -1</code>).</p>

<p>Return <code>true</code> <em>if the given array </em><em>represents the preorder traversal of some tree, and</em> <code>false</code> <em>otherwise.</em></p>

<p><strong>Note:</strong> the <strong>preorder</strong> traversal of a tree is a recursive way to traverse a tree in which we first visit the current node, then we do the preorder traversal for the left child, and finally, we do it for the right child.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nodes = [[0,-1],[1,0],[2,0],[3,2],[4,2]]
<strong>Output:</strong> true
<strong>Explanation:</strong> The given nodes make the tree in the picture below.
We can show that this is the preorder traversal of the tree, first we visit node 0, then we do the preorder traversal of the right child which is [1], then we do the preorder traversal of the left child which is [2,3,4].
</pre>

<p><img alt="" src="https://spcdn.pages.dev/leetcode/problems/2764.Is%20Array%20a%20Preorder%20of%20Some%20%E2%80%8CBinary%20Tree/images/1.png" style="padding: 10px; background: #fff; border-radius: .5rem; width: 250px; height: 251px;" /></p>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nodes = [[0,-1],[1,0],[2,0],[3,1],[4,1]]
<strong>Output:</strong> false
<strong>Explanation:</strong> The given nodes make the tree in the picture below.
For the preorder traversal, first we visit node 0, then we do the preorder traversal of the right child which is [1,3,4], but we can see that in the given order, 2 comes between 1 and 3, so, it&#39;s not the preorder traversal of the tree.
</pre>

<p><img alt="" src="https://spcdn.pages.dev/leetcode/problems/2764.Is%20Array%20a%20Preorder%20of%20Some%20%E2%80%8CBinary%20Tree/images/2.png" style="padding: 10px; background: #fff; border-radius: .5rem; width: 250px; height: 251px;" /></p>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nodes.length &lt;= 10<sup>5</sup></code></li>
	<li><code>nodes[i].length == 2</code></li>
	<li><code>0 &lt;= nodes[i][0] &lt;= 10<sup>5</sup></code></li>
	<li><code>-1 &lt;= nodes[i][1] &lt;= 10<sup>5</sup></code></li>
	<li>The input is generated such that <code>nodes</code> make a binary tree.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def isPreorder(self, nodes: List[List[int]]) -> bool:
        def dfs(i: int) -> int:
            nonlocal k
            if i != nodes[k][0]:
                return False
            k += 1
            return all(dfs(j) for j in g[i])

        g = defaultdict(list)
        for i, p in nodes:
            g[p].append(i)
        k = 0
        return dfs(nodes[0][0]) and k == len(nodes)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    private Map<Integer, List<Integer>> g = new HashMap<>();
    private List<List<Integer>> nodes;
    private int k;

    public boolean isPreorder(List<List<Integer>> nodes) {
        this.nodes = nodes;
        for (var node : nodes) {
            g.computeIfAbsent(node.get(1), key -> new ArrayList<>()).add(node.get(0));
        }
        return dfs(nodes.get(0).get(0)) && k == nodes.size();
    }

    private boolean dfs(int i) {
        if (i != nodes.get(k).get(0)) {
            return false;
        }
        ++k;
        for (int j : g.getOrDefault(i, List.of())) {
            if (!dfs(j)) {
                return false;
            }
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
    bool isPreorder(vector<vector<int>>& nodes) {
        int k = 0;
        unordered_map<int, vector<int>> g;
        for (auto& node : nodes) {
            g[node[1]].push_back(node[0]);
        }
        function<bool(int)> dfs = [&](int i) {
            if (i != nodes[k][0]) {
                return false;
            }
            ++k;
            for (int j : g[i]) {
                if (!dfs(j)) {
                    return false;
                }
            }
            return true;
        };
        return dfs(nodes[0][0]) && k == nodes.size();
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func isPreorder(nodes [][]int) bool {
	k := 0
	g := map[int][]int{}
	for _, node := range nodes {
		g[node[1]] = append(g[node[1]], node[0])
	}
	var dfs func(int) bool
	dfs = func(i int) bool {
		if i != nodes[k][0] {
			return false
		}
		k++
		for _, j := range g[i] {
			if !dfs(j) {
				return false
			}
		}
		return true
	}
	return dfs(nodes[0][0]) && k == len(nodes)
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function isPreorder(nodes: number[][]): boolean {
    let k = 0;
    const g: Map<number, number[]> = new Map();
    for (const [i, p] of nodes) {
        if (!g.has(p)) {
            g.set(p, []);
        }
        g.get(p)!.push(i);
    }
    const dfs = (i: number): boolean => {
        if (i !== nodes[k][0]) {
            return false;
        }
        ++k;
        for (const j of g.get(i) ?? []) {
            if (!dfs(j)) {
                return false;
            }
        }
        return true;
    };
    return dfs(nodes[0][0]) && k === nodes.length;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
