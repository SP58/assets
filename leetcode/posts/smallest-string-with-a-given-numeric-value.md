---
title: Smallest String With A Given Numeric Value
summary: Smallest String With A Given Numeric Value - Solution Explained
url: "/posts/smallest-string-with-a-given-numeric-value"
date: 2020-09-16T17:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Smallest String With A Given Numeric Value LeetCode Solution Explained in all languages", "1663", "leetcode question 1663", "Smallest String With A Given Numeric Value", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/smallest-string-with-a-given-numeric-value.webp
    alt: Smallest String With A Given Numeric Value - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1663. Smallest String With A Given Numeric Value](https://leetcode.com/problems/smallest-string-with-a-given-numeric-value)


## Description

<p>The <strong>numeric value</strong> of a <strong>lowercase character</strong> is defined as its position <code>(1-indexed)</code> in the alphabet, so the numeric value of <code>a</code> is <code>1</code>, the numeric value of <code>b</code> is <code>2</code>, the numeric value of <code>c</code> is <code>3</code>, and so on.</p>

<p>The <strong>numeric value</strong> of a <strong>string</strong> consisting of lowercase characters is defined as the sum of its characters&#39; numeric values. For example, the numeric value of the string <code>&quot;abe&quot;</code> is equal to <code>1 + 2 + 5 = 8</code>.</p>

<p>You are given two integers <code>n</code> and <code>k</code>. Return <em>the <strong>lexicographically smallest string</strong> with <strong>length</strong> equal to <code>n</code> and <strong>numeric value</strong> equal to <code>k</code>.</em></p>

<p>Note that a string <code>x</code> is lexicographically smaller than string <code>y</code> if <code>x</code> comes before <code>y</code> in dictionary order, that is, either <code>x</code> is a prefix of <code>y</code>, or if <code>i</code> is the first position such that <code>x[i] != y[i]</code>, then <code>x[i]</code> comes before <code>y[i]</code> in alphabetic order.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3, k = 27
<strong>Output:</strong> &quot;aay&quot;
<strong>Explanation:</strong> The numeric value of the string is 1 + 1 + 25 = 27, and it is the smallest string with such a value and length equal to 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 5, k = 73
<strong>Output:</strong> &quot;aaszz&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>n &lt;= k &lt;= 26 * n</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def getSmallestString(self, n: int, k: int) -> str:
        ans = ['a'] * n
        i, d = n - 1, k - n
        while d > 25:
            ans[i] = 'z'
            d -= 25
            i -= 1
        ans[i] = chr(ord(ans[i]) + d)
        return ''.join(ans)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public String getSmallestString(int n, int k) {
        char[] ans = new char[n];
        Arrays.fill(ans, 'a');
        int i = n - 1, d = k - n;
        for (; d > 25; d -= 25) {
            ans[i--] = 'z';
        }
        ans[i] = (char) ('a' + d);
        return String.valueOf(ans);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    string getSmallestString(int n, int k) {
        string ans(n, 'a');
        int i = n - 1, d = k - n;
        for (; d > 25; d -= 25) {
            ans[i--] = 'z';
        }
        ans[i] += d;
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func getSmallestString(n int, k int) string {
	ans := make([]byte, n)
	for i := range ans {
		ans[i] = 'a'
	}
	i, d := n-1, k-n
	for ; d > 25; i, d = i-1, d-25 {
		ans[i] = 'z'
	}
	ans[i] += byte(d)
	return string(ans)
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
