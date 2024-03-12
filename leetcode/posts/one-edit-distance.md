---
title: One Edit Distance
summary: One Edit Distance - Solution Explained
url: "/posts/one-edit-distance"
date: 2020-11-18T07:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["One Edit Distance LeetCode Solution Explained in all languages", "161", "leetcode question 161", "One Edit Distance", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/one-edit-distance.webp
    alt: One Edit Distance - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [161. One Edit Distance](https://leetcode.com/problems/one-edit-distance)


## Description

<p>Given two strings <code>s</code> and <code>t</code>, return <code>true</code> if they are both one edit distance apart, otherwise return <code>false</code>.</p>

<p>A string <code>s</code> is said to be one distance apart from a string <code>t</code> if you can:</p>

<ul>
	<li>Insert <strong>exactly one</strong> character into <code>s</code> to get <code>t</code>.</li>
	<li>Delete <strong>exactly one</strong> character from <code>s</code> to get <code>t</code>.</li>
	<li>Replace <strong>exactly one</strong> character of <code>s</code> with <strong>a different character</strong> to get <code>t</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ab&quot;, t = &quot;acb&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> We can insert &#39;c&#39; into s&nbsp;to get&nbsp;t.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;&quot;, t = &quot;&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> We cannot get t from s by only one step.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length, t.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> and <code>t</code> consist of lowercase letters, uppercase letters, and digits.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def isOneEditDistance(self, s: str, t: str) -> bool:
        if len(s) < len(t):
            return self.isOneEditDistance(t, s)
        m, n = len(s), len(t)
        if m - n > 1:
            return False
        for i, c in enumerate(t):
            if c != s[i]:
                return s[i + 1 :] == t[i + 1 :] if m == n else s[i + 1 :] == t[i:]
        return m == n + 1
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean isOneEditDistance(String s, String t) {
        int m = s.length(), n = t.length();
        if (m < n) {
            return isOneEditDistance(t, s);
        }
        if (m - n > 1) {
            return false;
        }
        for (int i = 0; i < n; ++i) {
            if (s.charAt(i) != t.charAt(i)) {
                if (m == n) {
                    return s.substring(i + 1).equals(t.substring(i + 1));
                }
                return s.substring(i + 1).equals(t.substring(i));
            }
        }
        return m == n + 1;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool isOneEditDistance(string s, string t) {
        int m = s.size(), n = t.size();
        if (m < n) return isOneEditDistance(t, s);
        if (m - n > 1) return false;
        for (int i = 0; i < n; ++i) {
            if (s[i] != t[i]) {
                if (m == n) return s.substr(i + 1) == t.substr(i + 1);
                return s.substr(i + 1) == t.substr(i);
            }
        }
        return m == n + 1;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func isOneEditDistance(s string, t string) bool {
	m, n := len(s), len(t)
	if m < n {
		return isOneEditDistance(t, s)
	}
	if m-n > 1 {
		return false
	}
	for i := range t {
		if s[i] != t[i] {
			if m == n {
				return s[i+1:] == t[i+1:]
			}
			return s[i+1:] == t[i:]
		}
	}
	return m == n+1
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
