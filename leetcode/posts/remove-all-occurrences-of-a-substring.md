---
title: Remove All Occurrences of a Substring
summary: Remove All Occurrences of a Substring - Solution Explained
url: "/posts/remove-all-occurrences-of-a-substring"
date: 2020-09-06T10:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Remove All Occurrences of a Substring LeetCode Solution Explained in all languages", "1910", "leetcode question 1910", "Remove All Occurrences of a Substring", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/remove-all-occurrences-of-a-substring.webp
    alt: Remove All Occurrences of a Substring - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1910. Remove All Occurrences of a Substring](https://leetcode.com/problems/remove-all-occurrences-of-a-substring)


## Description

<p>Given two strings <code>s</code> and <code>part</code>, perform the following operation on <code>s</code> until <strong>all</strong> occurrences of the substring <code>part</code> are removed:</p>

<ul>
	<li>Find the <strong>leftmost</strong> occurrence of the substring <code>part</code> and <strong>remove</strong> it from <code>s</code>.</li>
</ul>

<p>Return <code>s</code><em> after removing all occurrences of </em><code>part</code>.</p>

<p>A <strong>substring</strong> is a contiguous sequence of characters in a string.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;daabcbaabcbc&quot;, part = &quot;abc&quot;
<strong>Output:</strong> &quot;dab&quot;
<strong>Explanation</strong>: The following operations are done:
- s = &quot;da<strong><u>abc</u></strong>baabcbc&quot;, remove &quot;abc&quot; starting at index 2, so s = &quot;dabaabcbc&quot;.
- s = &quot;daba<strong><u>abc</u></strong>bc&quot;, remove &quot;abc&quot; starting at index 4, so s = &quot;dababc&quot;.
- s = &quot;dab<strong><u>abc</u></strong>&quot;, remove &quot;abc&quot; starting at index 3, so s = &quot;dab&quot;.
Now s has no occurrences of &quot;abc&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;axxxxyyyyb&quot;, part = &quot;xy&quot;
<strong>Output:</strong> &quot;ab&quot;
<strong>Explanation</strong>: The following operations are done:
- s = &quot;axxx<strong><u>xy</u></strong>yyyb&quot;, remove &quot;xy&quot; starting at index 4 so s = &quot;axxxyyyb&quot;.
- s = &quot;axx<strong><u>xy</u></strong>yyb&quot;, remove &quot;xy&quot; starting at index 3 so s = &quot;axxyyb&quot;.
- s = &quot;ax<strong><u>xy</u></strong>yb&quot;, remove &quot;xy&quot; starting at index 2 so s = &quot;axyb&quot;.
- s = &quot;a<strong><u>xy</u></strong>b&quot;, remove &quot;xy&quot; starting at index 1 so s = &quot;ab&quot;.
Now s has no occurrences of &quot;xy&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>1 &lt;= part.length &lt;= 1000</code></li>
	<li><code>s</code>​​​​​​ and <code>part</code> consists of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def removeOccurrences(self, s: str, part: str) -> str:
        while part in s:
            s = s.replace(part, '', 1)
        return s
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public String removeOccurrences(String s, String part) {
        while (s.contains(part)) {
            s = s.replaceFirst(part, "");
        }
        return s;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    string removeOccurrences(string s, string part) {
        int m = part.size();
        while (s.find(part) != -1) {
            s = s.erase(s.find(part), m);
        }
        return s;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func removeOccurrences(s string, part string) string {
	for strings.Contains(s, part) {
		s = strings.Replace(s, part, "", 1)
	}
	return s
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function removeOccurrences(s: string, part: string): string {
    while (s.includes(part)) {
        s = s.replace(part, '');
    }
    return s;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
