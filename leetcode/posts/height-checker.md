---
title: Height Checker
summary: Height Checker - Solution Explained
url: "/posts/height-checker"
date: 2020-10-12T05:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Height Checker LeetCode Solution Explained in all languages", "1051", "leetcode question 1051", "Height Checker", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/height-checker.webp
    alt: Height Checker - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1051. Height Checker](https://leetcode.com/problems/height-checker)


## Description

<p>A school is trying to take an annual photo of all the students. The students are asked to stand in a single file line in <strong>non-decreasing order</strong> by height. Let this ordering be represented by the integer array <code>expected</code> where <code>expected[i]</code> is the expected height of the <code>i<sup>th</sup></code> student in line.</p>

<p>You are given an integer array <code>heights</code> representing the <strong>current order</strong> that the students are standing in. Each <code>heights[i]</code> is the height of the <code>i<sup>th</sup></code> student in line (<strong>0-indexed</strong>).</p>

<p>Return <em>the <strong>number of indices</strong> where </em><code>heights[i] != expected[i]</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> heights = [1,1,4,2,1,3]
<strong>Output:</strong> 3
<strong>Explanation:</strong> 
heights:  [1,1,<u>4</u>,2,<u>1</u>,<u>3</u>]
expected: [1,1,<u>1</u>,2,<u>3</u>,<u>4</u>]
Indices 2, 4, and 5 do not match.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> heights = [5,1,2,3,4]
<strong>Output:</strong> 5
<strong>Explanation:</strong>
heights:  [<u>5</u>,<u>1</u>,<u>2</u>,<u>3</u>,<u>4</u>]
expected: [<u>1</u>,<u>2</u>,<u>3</u>,<u>4</u>,<u>5</u>]
All indices do not match.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> heights = [1,2,3,4,5]
<strong>Output:</strong> 0
<strong>Explanation:</strong>
heights:  [1,2,3,4,5]
expected: [1,2,3,4,5]
All indices match.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= heights.length &lt;= 100</code></li>
	<li><code>1 &lt;= heights[i] &lt;= 100</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        expected = sorted(heights)
        return sum(a != b for a, b in zip(heights, expected))
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int heightChecker(int[] heights) {
        int[] expected = heights.clone();
        Arrays.sort(expected);
        int ans = 0;
        for (int i = 0; i < heights.length; ++i) {
            if (heights[i] != expected[i]) {
                ++ans;
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
    int heightChecker(vector<int>& heights) {
        vector<int> expected = heights;
        sort(expected.begin(), expected.end());
        int ans = 0;
        for (int i = 0; i < heights.size(); ++i) ans += heights[i] != expected[i];
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func heightChecker(heights []int) int {
	expected := make([]int, len(heights))
	copy(expected, heights)
	sort.Ints(expected)
	ans := 0
	for i, v := range heights {
		if v != expected[i] {
			ans++
		}
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        cnt = [0] * 101
        for h in heights:
            cnt[h] += 1
        ans = i = 0
        for j in range(1, 101):
            while cnt[j]:
                cnt[j] -= 1
                if heights[i] != j:
                    ans += 1
                i += 1
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int heightChecker(int[] heights) {
        int[] cnt = new int[101];
        for (int h : heights) {
            ++cnt[h];
        }
        int ans = 0;
        for (int i = 0, j = 0; i < 101; ++i) {
            while (cnt[i] > 0) {
                --cnt[i];
                if (heights[j++] != i) {
                    ++ans;
                }
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
    int heightChecker(vector<int>& heights) {
        vector<int> cnt(101);
        for (int& h : heights) ++cnt[h];
        int ans = 0;
        for (int i = 0, j = 0; i < 101; ++i) {
            while (cnt[i]) {
                --cnt[i];
                if (heights[j++] != i) ++ans;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func heightChecker(heights []int) int {
	cnt := make([]int, 101)
	for _, h := range heights {
		cnt[h]++
	}
	ans := 0
	for i, j := 0, 0; i < 101; i++ {
		for cnt[i] > 0 {
			cnt[i]--
			if heights[j] != i {
				ans++
			}
			j++
		}
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
