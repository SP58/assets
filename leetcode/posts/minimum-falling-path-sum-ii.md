---
title: Minimum Falling Path Sum II
summary: Minimum Falling Path Sum II - Solution Explained
url: "/posts/minimum-falling-path-sum-ii"
date: 2020-10-02T07:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Minimum Falling Path Sum II LeetCode Solution Explained in all languages", "1289", "leetcode question 1289", "Minimum Falling Path Sum II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/minimum-falling-path-sum-ii.webp
    alt: Minimum Falling Path Sum II - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1289. Minimum Falling Path Sum II](https://leetcode.com/problems/minimum-falling-path-sum-ii)


## Description

<p>Given an <code>n x n</code> integer matrix <code>grid</code>, return <em>the minimum sum of a <strong>falling path with non-zero shifts</strong></em>.</p>

<p>A <strong>falling path with non-zero shifts</strong> is a choice of exactly one element from each row of <code>grid</code> such that no two elements chosen in adjacent rows are in the same column.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1289.Minimum%20Falling%20Path%20Sum%20II/images/falling-grid.jpg" style="width: 244px; height: 245px;" />
<pre>
<strong>Input:</strong> grid = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> 13
<strong>Explanation:</strong> 
The possible falling paths are:
[1,5,9], [1,5,7], [1,6,7], [1,6,8],
[2,4,8], [2,4,9], [2,6,7], [2,6,8],
[3,4,8], [3,4,9], [3,5,7], [3,5,9]
The falling path with the smallest sum is&nbsp;[1,5,7], so the answer is&nbsp;13.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[7]]
<strong>Output:</strong> 7
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 200</code></li>
	<li><code>-99 &lt;= grid[i][j] &lt;= 99</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def minFallingPathSum(self, grid: List[List[int]]) -> int:
        n = len(grid)
        f = [[0] * n for _ in range(n + 1)]
        for i, row in enumerate(grid, 1):
            for j, v in enumerate(row):
                x = min((f[i - 1][k] for k in range(n) if k != j), default=0)
                f[i][j] = v + x
        return min(f[n])
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int minFallingPathSum(int[][] grid) {
        int n = grid.length;
        int[][] f = new int[n + 1][n];
        final int inf = 1 << 30;
        for (int i = 1; i <= n; ++i) {
            for (int j = 0; j < n; ++j) {
                int x = inf;
                for (int k = 0; k < n; ++k) {
                    if (k != j) {
                        x = Math.min(x, f[i - 1][k]);
                    }
                }
                f[i][j] = grid[i - 1][j] + (x == inf ? 0 : x);
            }
        }
        int ans = inf;
        for (int x : f[n]) {
            ans = Math.min(ans, x);
        }
        return ans;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int minFallingPathSum(vector<vector<int>>& grid) {
        int n = grid.size();
        int f[n + 1][n];
        memset(f, 0, sizeof(f));
        const int inf = 1 << 30;
        for (int i = 1; i <= n; ++i) {
            for (int j = 0; j < n; ++j) {
                int x = inf;
                for (int k = 0; k < n; ++k) {
                    if (k != j) {
                        x = min(x, f[i - 1][k]);
                    }
                }
                f[i][j] = grid[i - 1][j] + (x == inf ? 0 : x);
            }
        }
        return *min_element(f[n], f[n] + n);
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func minFallingPathSum(grid [][]int) int {
	n := len(grid)
	f := make([][]int, n+1)
	for i := range f {
		f[i] = make([]int, n)
	}
	const inf = 1 << 30
	for i, row := range grid {
		i++
		for j, v := range row {
			x := inf
			for k := range row {
				if k != j {
					x = min(x, f[i-1][k])
				}
			}
			if x == inf {
				x = 0
			}
			f[i][j] = v + x
		}
	}
	return slices.Min(f[n])
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def minFallingPathSum(self, grid: List[List[int]]) -> int:
        f = g = 0
        fp = -1
        for row in grid:
            ff = gg = inf
            ffp = -1
            for j, v in enumerate(row):
                s = (g if j == fp else f) + v
                if s < ff:
                    gg = ff
                    ff = s
                    ffp = j
                elif s < gg:
                    gg = s
            f, g, fp = ff, gg, ffp
        return f
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int minFallingPathSum(int[][] grid) {
        int f = 0, g = 0;
        int fp = -1;
        final int inf = 1 << 30;
        for (int[] row : grid) {
            int ff = inf, gg = inf;
            int ffp = -1;
            for (int j = 0; j < row.length; ++j) {
                int s = (j != fp ? f : g) + row[j];
                if (s < ff) {
                    gg = ff;
                    ff = s;
                    ffp = j;
                } else if (s < gg) {
                    gg = s;
                }
            }
            f = ff;
            g = gg;
            fp = ffp;
        }
        return f;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int minFallingPathSum(vector<vector<int>>& grid) {
        int n = grid.size();
        int f = 0, g = 0, fp = -1;
        const int inf = 1 << 30;
        for (auto& row : grid) {
            int ff = inf, gg = inf;
            int ffp = -1;
            for (int j = 0; j < n; ++j) {
                int s = (fp != j ? f : g) + row[j];
                if (s < ff) {
                    gg = ff;
                    ff = s;
                    ffp = j;
                } else if (s < gg) {
                    gg = s;
                }
            }
            f = ff;
            g = gg;
            fp = ffp;
        }
        return f;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func minFallingPathSum(grid [][]int) int {
	const inf = 1 << 30
	f, g := 0, 0
	fp := -1
	for _, row := range grid {
		ff, gg := inf, inf
		ffp := -1
		for j, v := range row {
			s := f
			if j == fp {
				s = g
			}
			s += v
			if s < ff {
				ff, gg, ffp = s, ff, j
			} else if s < gg {
				gg = s
			}
		}
		f, g, fp = ff, gg, ffp
	}
	return f
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
