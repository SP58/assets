---
title: Convert a Number to Hexadecimal
summary: Convert a Number to Hexadecimal - Solution Explained
url: "/posts/convert-a-number-to-hexadecimal"
date: 2020-11-08T03:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Convert a Number to Hexadecimal LeetCode Solution Explained in all languages", "405", "leetcode question 405", "Convert a Number to Hexadecimal", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/convert-a-number-to-hexadecimal.webp
    alt: Convert a Number to Hexadecimal - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [405. Convert a Number to Hexadecimal](https://leetcode.com/problems/convert-a-number-to-hexadecimal)


## Description

<p>Given an integer <code>num</code>, return <em>a string representing its hexadecimal representation</em>. For negative integers, <a href="https://en.wikipedia.org/wiki/Two%27s_complement" target="_blank">two&rsquo;s complement</a> method is used.</p>

<p>All the letters in the answer string should be lowercase characters, and there should not be any leading zeros in the answer except for the zero itself.</p>

<p><strong>Note:&nbsp;</strong>You are not allowed to use any built-in library method to directly solve this problem.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> num = 26
<strong>Output:</strong> "1a"
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> num = -1
<strong>Output:</strong> "ffffffff"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;= num &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def toHex(self, num: int) -> str:
        if num == 0:
            return '0'
        chars = '0123456789abcdef'
        s = []
        for i in range(7, -1, -1):
            x = (num >> (4 * i)) & 0xF
            if s or x != 0:
                s.append(chars[x])
        return ''.join(s)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public String toHex(int num) {
        if (num == 0) {
            return "0";
        }
        StringBuilder sb = new StringBuilder();
        while (num != 0) {
            int x = num & 15;
            if (x < 10) {
                sb.append(x);
            } else {
                sb.append((char) (x - 10 + 'a'));
            }
            num >>>= 4;
        }
        return sb.reverse().toString();
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    string toHex(int num) {
        if (num == 0) return "0";
        string s = "";
        for (int i = 7; i >= 0; --i) {
            int x = (num >> (4 * i)) & 0xf;
            if (s.size() > 0 || x != 0) {
                char c = x < 10 ? (char) (x + '0') : (char) (x - 10 + 'a');
                s += c;
            }
        }
        return s;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func toHex(num int) string {
	if num == 0 {
		return "0"
	}
	sb := &strings.Builder{}
	for i := 7; i >= 0; i-- {
		x := num >> (4 * i) & 0xf
		if x > 0 || sb.Len() > 0 {
			var c byte
			if x < 10 {
				c = '0' + byte(x)
			} else {
				c = 'a' + byte(x-10)
			}
			sb.WriteByte(c)
		}
	}
	return sb.String()
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Java Code" >}}
```java
class Solution {
    public String toHex(int num) {
        if (num == 0) {
            return "0";
        }
        StringBuilder sb = new StringBuilder();
        for (int i = 7; i >= 0; --i) {
            int x = (num >> (4 * i)) & 0xf;
            if (sb.length() > 0 || x != 0) {
                char c = x < 10 ? (char) (x + '0') : (char) (x - 10 + 'a');
                sb.append(c);
            }
        }
        return sb.toString();
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
