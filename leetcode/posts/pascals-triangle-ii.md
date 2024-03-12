---
title: Pascal's Triangle II
summary: Pascal's Triangle II - Solution Explained
url: "/posts/pascals-triangle-ii"
date: 2020-11-20T01:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Pascal's Triangle II LeetCode Solution Explained in all languages", "119", "leetcode question 119", "Pascal's Triangle II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/pascals-triangle-ii.webp
    alt: Pascal's Triangle II - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [119. Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii)


## Description

<p>Given an integer <code>rowIndex</code>, return the <code>rowIndex<sup>th</sup></code> (<strong>0-indexed</strong>) row of the <strong>Pascal&#39;s triangle</strong>.</p>

<p>In <strong>Pascal&#39;s triangle</strong>, each number is the sum of the two numbers directly above it as shown:</p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0119.Pascal%27s%20Triangle%20II/images/PascalTriangleAnimated2.gif" style="height:240px; width:260px" />
<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> rowIndex = 3
<strong>Output:</strong> [1,3,3,1]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> rowIndex = 0
<strong>Output:</strong> [1]
</pre><p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> rowIndex = 1
<strong>Output:</strong> [1,1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= rowIndex &lt;= 33</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you optimize your algorithm to use only <code>O(rowIndex)</code> extra space?</p>

## Solutions

### Solution 1: Recursion

We create an array $f$ of length $rowIndex + 1$, initially all elements are $1$.

Next, starting from the second row, we calculate the value of the $j$th element in the current row from back to front, $f[j] = f[j] + f[j - 1]$, where $j \in [1, i - 1]$.

Finally, return $f$.

The time complexity is $O(n^2)$, and the space complexity is $O(n)$. Here, $n$ is the given number of rows.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        f = [1] * (rowIndex + 1)
        for i in range(2, rowIndex + 1):
            for j in range(i - 1, 0, -1):
                f[j] += f[j - 1]
        return f
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> f = new ArrayList<>();
        for (int i = 0; i < rowIndex + 1; ++i) {
            f.add(1);
        }
        for (int i = 2; i < rowIndex + 1; ++i) {
            for (int j = i - 1; j > 0; --j) {
                f.set(j, f.get(j) + f.get(j - 1));
            }
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
    vector<int> getRow(int rowIndex) {
        vector<int> f(rowIndex + 1, 1);
        for (int i = 2; i < rowIndex + 1; ++i) {
            for (int j = i - 1; j; --j) {
                f[j] += f[j - 1];
            }
        }
        return f;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func getRow(rowIndex int) []int {
	f := make([]int, rowIndex+1)
	for i := range f {
		f[i] = 1
	}
	for i := 2; i < rowIndex+1; i++ {
		for j := i - 1; j > 0; j-- {
			f[j] += f[j-1]
		}
	}
	return f
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function getRow(rowIndex: number): number[] {
    const f: number[] = Array(rowIndex + 1).fill(1);
    for (let i = 2; i < rowIndex + 1; ++i) {
        for (let j = i - 1; j; --j) {
            f[j] += f[j - 1];
        }
    }
    return f;
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn get_row(row_index: i32) -> Vec<i32> {
        let n = (row_index + 1) as usize;
        let mut f = vec![1; n];
        for i in 2..n {
            for j in (1..i).rev() {
                f[j] += f[j - 1];
            }
        }
        f
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
