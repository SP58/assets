---
title: Reverse Words in a String III
summary: Reverse Words in a String III - Solution Explained
url: "/posts/reverse-words-in-a-string-iii"
date: 2020-11-01T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Reverse Words in a String III LeetCode Solution Explained in all languages", "557", "leetcode question 557", "Reverse Words in a String III", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/reverse-words-in-a-string-iii.webp
    alt: Reverse Words in a String III - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii)


## Description

<p>Given a string <code>s</code>, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Let&#39;s take LeetCode contest&quot;
<strong>Output:</strong> &quot;s&#39;teL ekat edoCteeL tsetnoc&quot;
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Mr Ding&quot;
<strong>Output:</strong> &quot;rM gniD&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> contains printable <strong>ASCII</strong> characters.</li>
	<li><code>s</code> does not contain any leading or trailing spaces.</li>
	<li>There is <strong>at least one</strong> word in <code>s</code>.</li>
	<li>All the words in <code>s</code> are separated by a single space.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join([t[::-1] for t in s.split(' ')])
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public String reverseWords(String s) {
        StringBuilder res = new StringBuilder();
        for (String t : s.split(" ")) {
            for (int i = t.length() - 1; i >= 0; --i) {
                res.append(t.charAt(i));
            }
            res.append(" ");
        }
        return res.substring(0, res.length() - 1);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    string reverseWords(string s) {
        for (int i = 0, n = s.size(); i < n; ++i) {
            int j = i;
            while (++j < n && s[j] != ' ')
                ;
            reverse(s.begin() + i, s.begin() + j);
            i = j;
        }
        return s;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func reverseWords(s string) string {
	t := []byte(s)
	for i := 0; i < len(t); i++ {
		j := i
		for j < len(t) && t[j] != ' ' {
			j++
		}
		for st, ed := i, j-1; st < ed; st, ed = st+1, ed-1 {
			t[st], t[ed] = t[ed], t[st]
		}
		i = j
	}
	return string(t)
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function reverseWords(s: string): string {
    return s
        .split(/\s+/)
        .map(str => {
            let res = '';
            for (const c of str) {
                res = c + res;
            }
            return res;
        })
        .join(' ');
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn reverse_words(s: String) -> String {
        s.split(' ')
            .map(|s| s.chars().rev().collect::<String>())
            .collect::<Vec<_>>()
            .join(" ")
    }
}
```
{{< /terminal >}}

{{< terminal title="PHP Code" >}}
```php
class Solution {
    /**
     * @param String $s
     * @return String
     */
    function reverseWords($s) {
        $sArr = explode(' ', $s);
        for ($i = 0; $i < count($sArr); $i++) {
            $sArr[$i] = strrev($sArr[$i]);
        }
        return implode(' ', $sArr);
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
