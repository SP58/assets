---
title: Swap Adjacent in LR String
summary: Swap Adjacent in LR String - Solution Explained
url: "/posts/swap-adjacent-in-lr-string"
date: 2020-10-23T15:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Swap Adjacent in LR String LeetCode Solution Explained in all languages", "777", "leetcode question 777", "Swap Adjacent in LR String", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/swap-adjacent-in-lr-string.webp
    alt: Swap Adjacent in LR String - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [777. Swap Adjacent in LR String](https://leetcode.com/problems/swap-adjacent-in-lr-string)


## Description

<p>In a string composed of <code>&#39;L&#39;</code>, <code>&#39;R&#39;</code>, and <code>&#39;X&#39;</code> characters, like <code>&quot;RXXLRXRXL&quot;</code>, a move consists of either replacing one occurrence of <code>&quot;XL&quot;</code> with <code>&quot;LX&quot;</code>, or replacing one occurrence of <code>&quot;RX&quot;</code> with <code>&quot;XR&quot;</code>. Given the starting string <code>start</code> and the ending string <code>end</code>, return <code>True</code> if and only if there exists a sequence of moves to transform one string to the other.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> start = &quot;RXXLRXRXL&quot;, end = &quot;XRLXXRRLX&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> We can transform start to end following these steps:
RXXLRXRXL -&gt;
XRXLRXRXL -&gt;
XRLXRXRXL -&gt;
XRLXXRRXL -&gt;
XRLXXRRLX
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> start = &quot;X&quot;, end = &quot;L&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= start.length&nbsp;&lt;= 10<sup>4</sup></code></li>
	<li><code>start.length == end.length</code></li>
	<li>Both <code>start</code> and <code>end</code> will only consist of characters in <code>&#39;L&#39;</code>, <code>&#39;R&#39;</code>, and&nbsp;<code>&#39;X&#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def canTransform(self, start: str, end: str) -> bool:
        n = len(start)
        i = j = 0
        while 1:
            while i < n and start[i] == 'X':
                i += 1
            while j < n and end[j] == 'X':
                j += 1
            if i >= n and j >= n:
                return True
            if i >= n or j >= n or start[i] != end[j]:
                return False
            if start[i] == 'L' and i < j:
                return False
            if start[i] == 'R' and i > j:
                return False
            i, j = i + 1, j + 1
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean canTransform(String start, String end) {
        int n = start.length();
        int i = 0, j = 0;
        while (true) {
            while (i < n && start.charAt(i) == 'X') {
                ++i;
            }
            while (j < n && end.charAt(j) == 'X') {
                ++j;
            }
            if (i == n && j == n) {
                return true;
            }
            if (i == n || j == n || start.charAt(i) != end.charAt(j)) {
                return false;
            }
            if (start.charAt(i) == 'L' && i < j || start.charAt(i) == 'R' && i > j) {
                return false;
            }
            ++i;
            ++j;
        }
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool canTransform(string start, string end) {
        int n = start.size();
        int i = 0, j = 0;
        while (true) {
            while (i < n && start[i] == 'X') ++i;
            while (j < n && end[j] == 'X') ++j;
            if (i == n && j == n) return true;
            if (i == n || j == n || start[i] != end[j]) return false;
            if (start[i] == 'L' && i < j) return false;
            if (start[i] == 'R' && i > j) return false;
            ++i;
            ++j;
        }
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func canTransform(start string, end string) bool {
	n := len(start)
	i, j := 0, 0
	for {
		for i < n && start[i] == 'X' {
			i++
		}
		for j < n && end[j] == 'X' {
			j++
		}
		if i == n && j == n {
			return true
		}
		if i == n || j == n || start[i] != end[j] {
			return false
		}
		if start[i] == 'L' && i < j {
			return false
		}
		if start[i] == 'R' && i > j {
			return false
		}
		i, j = i+1, j+1
	}
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
