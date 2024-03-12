---
title: Pascal's Triangle
summary: Pascal's Triangle - Solution Explained
url: "/posts/pascals-triangle"
date: 2020-11-20T02:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Pascal's Triangle LeetCode Solution Explained in all languages", "118", "leetcode question 118", "Pascal's Triangle", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/pascals-triangle.webp
    alt: Pascal's Triangle - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle)


## Description

<p>Given an integer <code>numRows</code>, return the first numRows of <strong>Pascal&#39;s triangle</strong>.</p>

<p>In <strong>Pascal&#39;s triangle</strong>, each number is the sum of the two numbers directly above it as shown:</p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0118.Pascal%27s%20Triangle/images/PascalTriangleAnimated2.gif" style="height:240px; width:260px" />
<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> numRows = 5
<strong>Output:</strong> [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> numRows = 1
<strong>Output:</strong> [[1]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= numRows &lt;= 30</code></li>
</ul>

## Solutions

### Solution 1: Simulation

First, we create an answer array $f$, and then set the first row of $f$ to $[1]$. Next, starting from the second row, the first and last elements of each row are $1$, and the other elements are calculated by $f[i][j] = f[i - 1][j - 1] + f[i - 1][j]$.

The time complexity is $O(n^2)$, and the space complexity is $O(n^2)$. Here, $n$ is the number of rows.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        f = [[1]]
        for i in range(numRows - 1):
            g = [1] + [a + b for a, b in pairwise(f[-1])] + [1]
            f.append(g)
        return f
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> f = new ArrayList<>();
        f.add(List.of(1));
        for (int i = 0; i < numRows - 1; ++i) {
            List<Integer> g = new ArrayList<>();
            g.add(1);
            for (int j = 0; j < f.get(i).size() - 1; ++j) {
                g.add(f.get(i).get(j) + f.get(i).get(j + 1));
            }
            g.add(1);
            f.add(g);
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
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> f;
        f.push_back(vector<int>(1, 1));
        for (int i = 0; i < numRows - 1; ++i) {
            vector<int> g;
            g.push_back(1);
            for (int j = 0; j < f[i].size() - 1; ++j) {
                g.push_back(f[i][j] + f[i][j + 1]);
            }
            g.push_back(1);
            f.push_back(g);
        }
        return f;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func generate(numRows int) [][]int {
	f := [][]int{[]int{1}}
	for i := 0; i < numRows-1; i++ {
		g := []int{1}
		for j := 0; j < len(f[i])-1; j++ {
			g = append(g, f[i][j]+f[i][j+1])
		}
		g = append(g, 1)
		f = append(f, g)
	}
	return f
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function generate(numRows: number): number[][] {
    const f: number[][] = [[1]];
    for (let i = 0; i < numRows - 1; ++i) {
        const g: number[] = [1];
        for (let j = 0; j < f[i].length - 1; ++j) {
            g.push(f[i][j] + f[i][j + 1]);
        }
        g.push(1);
        f.push(g);
    }
    return f;
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    #[allow(dead_code)]
    pub fn generate(num_rows: i32) -> Vec<Vec<i32>> {
        let mut ret_vec: Vec<Vec<i32>> = Vec::new();
        let mut cur_vec: Vec<i32> = Vec::new();

        for i in 0..num_rows as usize {
            let mut new_vec: Vec<i32> = vec![1; i + 1];
            for j in 1..i {
                new_vec[j] = cur_vec[j - 1] + cur_vec[j];
            }
            cur_vec = new_vec.clone();
            ret_vec.push(new_vec);
        }

        ret_vec
    }
}
```
{{< /terminal >}}

{{< terminal title="JavaScript Code" >}}
```js
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function (numRows) {
    const f = [[1]];
    for (let i = 0; i < numRows - 1; ++i) {
        const g = [1];
        for (let j = 0; j < f[i].length - 1; ++j) {
            g.push(f[i][j] + f[i][j + 1]);
        }
        g.push(1);
        f.push(g);
    }
    return f;
};
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
