---
title: Number of Segments in a String
summary: Number of Segments in a String - Solution Explained
url: "/posts/number-of-segments-in-a-string"
date: 2020-11-06T22:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Number of Segments in a String LeetCode Solution Explained in all languages", "434", "leetcode question 434", "Number of Segments in a String", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/number-of-segments-in-a-string.webp
    alt: Number of Segments in a String - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [434. Number of Segments in a String](https://leetcode.com/problems/number-of-segments-in-a-string)


## Description

<p>Given a string <code>s</code>, return <em>the number of segments in the string</em>.</p>

<p>A <strong>segment</strong> is defined to be a contiguous sequence of <strong>non-space characters</strong>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Hello, my name is John&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The five segments are [&quot;Hello,&quot;, &quot;my&quot;, &quot;name&quot;, &quot;is&quot;, &quot;John&quot;]
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Hello&quot;
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 300</code></li>
	<li><code>s</code> consists of lowercase and uppercase English letters, digits, or one of the following characters <code>&quot;!@#$%^&amp;*()_+-=&#39;,.:&quot;</code>.</li>
	<li>The only space character in <code>s</code> is <code>&#39; &#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def countSegments(self, s: str) -> int:
        return len(s.split())
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int countSegments(String s) {
        int ans = 0;
        for (String t : s.split(" ")) {
            if (!"".equals(t)) {
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
    int countSegments(string s) {
        int ans = 0;
        istringstream ss(s);
        while (ss >> s) ++ans;
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func countSegments(s string) int {
	ans := 0
	for _, t := range strings.Split(s, " ") {
		if len(t) > 0 {
			ans++
		}
	}
	return ans
}
```
{{< /terminal >}}

{{< terminal title="PHP Code" >}}
```php
class Solution {
    /**
     * @param String $s
     * @return Integer
     */
    function countSegments($s) {
        $arr = explode(' ', $s);
        $cnt = 0;
        for ($i = 0; $i < count($arr); $i++) {
            if (strlen($arr[$i]) != 0) {
                $cnt++;
            }
        }
        return $cnt;
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def countSegments(self, s: str) -> int:
        ans = 0
        for i, c in enumerate(s):
            if c != ' ' and (i == 0 or s[i - 1] == ' '):
                ans += 1
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int countSegments(String s) {
        int ans = 0;
        for (int i = 0; i < s.length(); ++i) {
            if (s.charAt(i) != ' ' && (i == 0 || s.charAt(i - 1) == ' ')) {
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
    int countSegments(string s) {
        int ans = 0;
        for (int i = 0; i < s.size(); ++i) {
            if (s[i] != ' ' && (i == 0 || s[i - 1] == ' ')) {
                ++ans;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func countSegments(s string) int {
	ans := 0
	for i, c := range s {
		if c != ' ' && (i == 0 || s[i-1] == ' ') {
			ans++
		}
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
