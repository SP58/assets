---
title: Row With Maximum Ones
summary: Row With Maximum Ones - Solution Explained
url: "/posts/row-with-maximum-ones"
date: 2020-08-06T21:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Row With Maximum Ones LeetCode Solution Explained in all languages", "2643", "leetcode question 2643", "Row With Maximum Ones", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/row-with-maximum-ones.webp
    alt: Row With Maximum Ones - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2643. Row With Maximum Ones](https://leetcode.com/problems/row-with-maximum-ones)


## Description

<p>Given a <code>m x n</code> binary matrix <code>mat</code>, find the <strong>0-indexed</strong> position of the row that contains the <strong>maximum</strong> count of <strong>ones,</strong> and the number of ones in that row.</p>

<p>In case there are multiple rows that have the maximum count of ones, the row with the <strong>smallest row number</strong> should be selected.</p>

<p>Return<em> an array containing the index of the row, and the number of ones in it.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> mat = [[0,1],[1,0]]
<strong>Output:</strong> [0,1]
<strong>Explanation:</strong> Both rows have the same number of 1&#39;s. So we return the index of the smaller row, 0, and the maximum count of ones (1<code>)</code>. So, the answer is [0,1]. 
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> mat = [[0,0,0],[0,1,1]]
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The row indexed 1 has the maximum count of ones <code>(2)</code>. So we return its index, <code>1</code>, and the count. So, the answer is [1,2].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> mat = [[0,0],[1,1],[0,0]]
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The row indexed 1 has the maximum count of ones (2). So the answer is [1,2].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code>&nbsp;</li>
	<li><code>n == mat[i].length</code>&nbsp;</li>
	<li><code>1 &lt;= m, n &lt;= 100</code>&nbsp;</li>
	<li><code>mat[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def rowAndMaximumOnes(self, mat: List[List[int]]) -> List[int]:
        ans = [0, 0]
        for i, row in enumerate(mat):
            cnt = row.count(1)
            if ans[1] < cnt:
                ans = [i, cnt]
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int[] rowAndMaximumOnes(int[][] mat) {
        int[] ans = new int[2];
        for (int i = 0; i < mat.length; ++i) {
            int cnt = 0;
            for (int x : mat[i]) {
                if (x == 1) {
                    ++cnt;
                }
            }
            if (ans[1] < cnt) {
                ans[0] = i;
                ans[1] = cnt;
            }
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
    vector<int> rowAndMaximumOnes(vector<vector<int>>& mat) {
        vector<int> ans(2);
        for (int i = 0; i < mat.size(); ++i) {
            int cnt = 0;
            for (auto& x : mat[i]) {
                cnt += x == 1;
            }
            if (ans[1] < cnt) {
                ans[0] = i;
                ans[1] = cnt;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func rowAndMaximumOnes(mat [][]int) []int {
	ans := make([]int, 2)
	for i, row := range mat {
		cnt := 0
		for _, x := range row {
			if x == 1 {
				cnt++
			}
		}
		if ans[1] < cnt {
			ans[0], ans[1] = i, cnt
		}
	}
	return ans
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function rowAndMaximumOnes(mat: number[][]): number[] {
    const ans: number[] = [0, 0];
    for (let i = 0; i < mat.length; ++i) {
        const cnt = mat[i].reduce((a, b) => a + b);
        if (ans[1] < cnt) {
            ans[0] = i;
            ans[1] = cnt;
        }
    }
    return ans;
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn row_and_maximum_ones(mat: Vec<Vec<i32>>) -> Vec<i32> {
        let mut ans = vec![0, 0];

        for (i, row) in mat.iter().enumerate() {
            let cnt = row
                .iter()
                .filter(|&v| *v == 1)
                .count() as i32;
            if ans[1] < cnt {
                ans[0] = i as i32;
                ans[1] = cnt;
            }
        }

        ans
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->