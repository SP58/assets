---
title: Regions Cut By Slashes
summary: Regions Cut By Slashes - Solution Explained
url: "/posts/regions-cut-by-slashes"
date: 2020-10-16T01:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Regions Cut By Slashes LeetCode Solution Explained in all languages", "959", "leetcode question 959", "Regions Cut By Slashes", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/regions-cut-by-slashes.webp
    alt: Regions Cut By Slashes - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [959. Regions Cut By Slashes](https://leetcode.com/problems/regions-cut-by-slashes)


## Description

<p>An <code>n x n</code> grid is composed of <code>1 x 1</code> squares where each <code>1 x 1</code> square consists of a <code>&#39;/&#39;</code>, <code>&#39;\&#39;</code>, or blank space <code>&#39; &#39;</code>. These characters divide the square into contiguous regions.</p>

<p>Given the grid <code>grid</code> represented as a string array, return <em>the number of regions</em>.</p>

<p>Note that backslash characters are escaped, so a <code>&#39;\&#39;</code> is represented as <code>&#39;\\&#39;</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0959.Regions%20Cut%20By%20Slashes/images/1.png" style="width: 200px; height: 200px;" />
<pre>
<strong>Input:</strong> grid = [&quot; /&quot;,&quot;/ &quot;]
<strong>Output:</strong> 2
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0959.Regions%20Cut%20By%20Slashes/images/2.png" style="width: 200px; height: 198px;" />
<pre>
<strong>Input:</strong> grid = [&quot; /&quot;,&quot;  &quot;]
<strong>Output:</strong> 1
</pre>

<p><strong class="example">Example 3:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0959.Regions%20Cut%20By%20Slashes/images/4.png" style="width: 200px; height: 200px;" />
<pre>
<strong>Input:</strong> grid = [&quot;/\\&quot;,&quot;\\/&quot;]
<strong>Output:</strong> 5
<strong>Explanation: </strong>Recall that because \ characters are escaped, &quot;\\/&quot; refers to \/, and &quot;/\\&quot; refers to /\.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 30</code></li>
	<li><code>grid[i][j]</code> is either <code>&#39;/&#39;</code>, <code>&#39;\&#39;</code>, or <code>&#39; &#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def regionsBySlashes(self, grid: List[str]) -> int:
        def find(x):
            if p[x] != x:
                p[x] = find(p[x])
            return p[x]

        def union(a, b):
            pa, pb = find(a), find(b)
            if pa != pb:
                p[pa] = pb
                nonlocal size
                size -= 1

        n = len(grid)
        size = n * n * 4
        p = list(range(size))
        for i, row in enumerate(grid):
            for j, v in enumerate(row):
                k = i * n + j
                if i < n - 1:
                    union(4 * k + 2, (k + n) * 4)
                if j < n - 1:
                    union(4 * k + 1, (k + 1) * 4 + 3)
                if v == '/':
                    union(4 * k, 4 * k + 3)
                    union(4 * k + 1, 4 * k + 2)
                elif v == '\\':
                    union(4 * k, 4 * k + 1)
                    union(4 * k + 2, 4 * k + 3)
                else:
                    union(4 * k, 4 * k + 1)
                    union(4 * k + 1, 4 * k + 2)
                    union(4 * k + 2, 4 * k + 3)
        return size
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    private int[] p;
    private int size;

    public int regionsBySlashes(String[] grid) {
        int n = grid.length;
        size = n * n * 4;
        p = new int[size];
        for (int i = 0; i < p.length; ++i) {
            p[i] = i;
        }
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                int k = i * n + j;
                if (i < n - 1) {
                    union(4 * k + 2, (k + n) * 4);
                }
                if (j < n - 1) {
                    union(4 * k + 1, (k + 1) * 4 + 3);
                }
                char v = grid[i].charAt(j);
                if (v == '/') {
                    union(4 * k, 4 * k + 3);
                    union(4 * k + 1, 4 * k + 2);
                } else if (v == '\\') {
                    union(4 * k, 4 * k + 1);
                    union(4 * k + 2, 4 * k + 3);
                } else {
                    union(4 * k, 4 * k + 1);
                    union(4 * k + 1, 4 * k + 2);
                    union(4 * k + 2, 4 * k + 3);
                }
            }
        }
        return size;
    }

    private int find(int x) {
        if (p[x] != x) {
            p[x] = find(p[x]);
        }
        return p[x];
    }

    private void union(int a, int b) {
        int pa = find(a);
        int pb = find(b);
        if (pa == pb) {
            return;
        }
        p[pa] = pb;
        --size;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    vector<int> p;
    int size;

    int regionsBySlashes(vector<string>& grid) {
        int n = grid.size();
        size = n * n * 4;
        p.resize(size);
        for (int i = 0; i < size; ++i) p[i] = i;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                int k = i * n + j;
                if (i < n - 1) merge(4 * k + 2, (k + n) * 4);
                if (j < n - 1) merge(4 * k + 1, (k + 1) * 4 + 3);
                char v = grid[i][j];
                if (v == '/') {
                    merge(4 * k, 4 * k + 3);
                    merge(4 * k + 1, 4 * k + 2);
                } else if (v == '\\') {
                    merge(4 * k, 4 * k + 1);
                    merge(4 * k + 2, 4 * k + 3);
                } else {
                    merge(4 * k, 4 * k + 1);
                    merge(4 * k + 1, 4 * k + 2);
                    merge(4 * k + 2, 4 * k + 3);
                }
            }
        }
        return size;
    }

    void merge(int a, int b) {
        int pa = find(a);
        int pb = find(b);
        if (pa == pb) return;
        p[pa] = pb;
        --size;
    }

    int find(int x) {
        if (p[x] != x) p[x] = find(p[x]);
        return p[x];
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func regionsBySlashes(grid []string) int {
	n := len(grid)
	size := n * n * 4
	p := make([]int, size)
	for i := range p {
		p[i] = i
	}
	var find func(x int) int
	find = func(x int) int {
		if p[x] != x {
			p[x] = find(p[x])
		}
		return p[x]
	}
	union := func(a, b int) {
		pa, pb := find(a), find(b)
		if pa == pb {
			return
		}
		p[pa] = pb
		size--
	}
	for i, row := range grid {
		for j, v := range row {
			k := i*n + j
			if i < n-1 {
				union(4*k+2, (k+n)*4)
			}
			if j < n-1 {
				union(4*k+1, (k+1)*4+3)
			}
			if v == '/' {
				union(4*k, 4*k+3)
				union(4*k+1, 4*k+2)
			} else if v == '\\' {
				union(4*k, 4*k+1)
				union(4*k+2, 4*k+3)
			} else {
				union(4*k, 4*k+1)
				union(4*k+1, 4*k+2)
				union(4*k+2, 4*k+3)
			}
		}
	}
	return size
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
