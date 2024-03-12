---
title: Bitwise AND of Numbers Range
summary: Bitwise AND of Numbers Range - Solution Explained
url: "/posts/bitwise-and-of-numbers-range"
date: 2020-11-16T15:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Bitwise AND of Numbers Range LeetCode Solution Explained in all languages", "201", "leetcode question 201", "Bitwise AND of Numbers Range", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/bitwise-and-of-numbers-range.webp
    alt: Bitwise AND of Numbers Range - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [201. Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range)


## Description

<p>Given two integers <code>left</code> and <code>right</code> that represent the range <code>[left, right]</code>, return <em>the bitwise AND of all numbers in this range, inclusive</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> left = 5, right = 7
<strong>Output:</strong> 4
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> left = 0, right = 0
<strong>Output:</strong> 0
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> left = 1, right = 2147483647
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= left &lt;= right &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def rangeBitwiseAnd(self, left: int, right: int) -> int:
        while left < right:
            right &= right - 1
        return right
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
        while (left < right) {
            right &= (right - 1);
        }
        return right;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int rangeBitwiseAnd(int left, int right) {
        while (left < right) {
            right &= (right - 1);
        }
        return right;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func rangeBitwiseAnd(left int, right int) int {
	for left < right {
		right &= (right - 1)
	}
	return right
}
```
{{< /terminal >}}

{{< terminal title="JavaScript Code" >}}
```js
/**
 * @param {number} left
 * @param {number} right
 * @return {number}
 */
var rangeBitwiseAnd = function (left, right) {
    while (left < right) {
        right &= right - 1;
    }
    return right;
};
```
{{< /terminal >}}

{{< terminal title="C# Code" >}}
```cs
public class Solution {
    public int RangeBitwiseAnd(int left, int right) {
        while (left < right) {
            right &= (right - 1);
        }
        return right;
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
