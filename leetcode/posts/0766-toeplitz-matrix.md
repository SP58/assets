---
title: 0766 Toeplitz Matrix
summary: 0766 Toeplitz Matrix LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0766 Toeplitz Matrix LeetCode Solution Explained in all languages", "0766 Toeplitz Matrix", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0766 Toeplitz Matrix - Solution Explained/problem-solving.webp
    alt: 0766 Toeplitz Matrix
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [766. Toeplitz Matrix](https://leetcode.com/problems/toeplitz-matrix)


## Description

<p>Given an <code>m x n</code> <code>matrix</code>, return&nbsp;<em><code>true</code>&nbsp;if the matrix is Toeplitz. Otherwise, return <code>false</code>.</em></p>

<p>A matrix is <strong>Toeplitz</strong> if every diagonal from top-left to bottom-right has the same elements.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0766.Toeplitz%20Matrix/images/ex1.jpg" style="width: 322px; height: 242px;" />
<pre>
<strong>Input:</strong> matrix = [[1,2,3,4],[5,1,2,3],[9,5,1,2]]
<strong>Output:</strong> true
<strong>Explanation:</strong>
In the above grid, the&nbsp;diagonals are:
&quot;[9]&quot;, &quot;[5, 5]&quot;, &quot;[1, 1, 1]&quot;, &quot;[2, 2, 2]&quot;, &quot;[3, 3]&quot;, &quot;[4]&quot;.
In each diagonal all elements are the same, so the answer is True.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0766.Toeplitz%20Matrix/images/ex2.jpg" style="width: 162px; height: 162px;" />
<pre>
<strong>Input:</strong> matrix = [[1,2],[2,2]]
<strong>Output:</strong> false
<strong>Explanation:</strong>
The diagonal &quot;[1, 2]&quot; has different elements.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 20</code></li>
	<li><code>0 &lt;= matrix[i][j] &lt;= 99</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>What if the <code>matrix</code> is stored on disk, and the memory is limited such that you can only load at most one row of the matrix into the memory at once?</li>
	<li>What if the <code>matrix</code> is so large that you can only load up a partial row into the memory at once?</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def isToeplitzMatrix(self, matrix: List[List[int]]) -> bool:
        m, n = len(matrix), len(matrix[0])
        return all(
            matrix[i][j] == matrix[i - 1][j - 1]
            for i in range(1, m)
            for j in range(1, n)
        )
```

```java
class Solution {
    public boolean isToeplitzMatrix(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                if (matrix[i][j] != matrix[i - 1][j - 1]) {
                    return false;
                }
            }
        }
        return true;
    }
}
```

```cpp
class Solution {
public:
    bool isToeplitzMatrix(vector<vector<int>>& matrix) {
        int m = matrix.size(), n = matrix[0].size();
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                if (matrix[i][j] != matrix[i - 1][j - 1]) {
                    return false;
                }
            }
        }
        return true;
    }
};
```

```go
func isToeplitzMatrix(matrix [][]int) bool {
	m, n := len(matrix), len(matrix[0])
	for i := 1; i < m; i++ {
		for j := 1; j < n; j++ {
			if matrix[i][j] != matrix[i-1][j-1] {
				return false
			}
		}
	}
	return true
}
```

```js
/**
 * @param {number[][]} matrix
 * @return {boolean}
 */
var isToeplitzMatrix = function (matrix) {
    const m = matrix.length;
    const n = matrix[0].length;
    for (let i = 1; i < m; ++i) {
        for (let j = 1; j < n; ++j) {
            if (matrix[i][j] != matrix[i - 1][j - 1]) {
                return false;
            }
        }
    }
    return true;
};
```

<!-- tabs:end -->

<!-- end -->