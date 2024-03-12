---
title: Minimum Changes To Make Alternating Binary String
summary: Minimum Changes To Make Alternating Binary String - Solution Explained
url: "/posts/minimum-changes-to-make-alternating-binary-string"
date: 2020-09-12T18:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Minimum Changes To Make Alternating Binary String LeetCode Solution Explained in all languages", "1758", "leetcode question 1758", "Minimum Changes To Make Alternating Binary String", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/minimum-changes-to-make-alternating-binary-string.webp
    alt: Minimum Changes To Make Alternating Binary String - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1758. Minimum Changes To Make Alternating Binary String](https://leetcode.com/problems/minimum-changes-to-make-alternating-binary-string)


## Description

<p>You are given a string <code>s</code> consisting only of the characters <code>&#39;0&#39;</code> and <code>&#39;1&#39;</code>. In one operation, you can change any <code>&#39;0&#39;</code> to <code>&#39;1&#39;</code> or vice versa.</p>

<p>The string is called alternating if no two adjacent characters are equal. For example, the string <code>&quot;010&quot;</code> is alternating, while the string <code>&quot;0100&quot;</code> is not.</p>

<p>Return <em>the <strong>minimum</strong> number of operations needed to make</em> <code>s</code> <em>alternating</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;0100&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> If you change the last character to &#39;1&#39;, s will be &quot;0101&quot;, which is alternating.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;10&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> s is already alternating.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1111&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> You need two operations to reach &quot;0101&quot; or &quot;1010&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s[i]</code> is either <code>&#39;0&#39;</code> or <code>&#39;1&#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def minOperations(self, s: str) -> int:
        cnt = sum(c != '01'[i & 1] for i, c in enumerate(s))
        return min(cnt, len(s) - cnt)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int minOperations(String s) {
        int cnt = 0, n = s.length();
        for (int i = 0; i < n; ++i) {
            cnt += (s.charAt(i) != "01".charAt(i & 1) ? 1 : 0);
        }
        return Math.min(cnt, n - cnt);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int minOperations(string s) {
        int cnt = 0, n = s.size();
        for (int i = 0; i < n; ++i) cnt += s[i] != "01"[i & 1];
        return min(cnt, n - cnt);
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func minOperations(s string) int {
	cnt := 0
	for i, c := range s {
		if c != []rune("01")[i&1] {
			cnt++
		}
	}
	return min(cnt, len(s)-cnt)
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function minOperations(s: string): number {
    const n = s.length;
    let count = 0;
    for (let i = 0; i < n; i++) {
        count += s[i] !== '01'[i & 1] ? 1 : 0;
    }
    return Math.min(count, n - count);
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn min_operations(s: String) -> i32 {
        let n = s.len();
        let s = s.as_bytes();
        let cs = [b'0', b'1'];
        let mut count = 0;
        for i in 0..n {
            count += if s[i] != cs[i & 1] { 1 } else { 0 };
        }
        count.min(n - count) as i32
    }
}
```
{{< /terminal >}}

{{< terminal title="C Code" >}}
```c
#define min(a, b) (((a) < (b)) ? (a) : (b))

int minOperations(char* s) {
    int n = strlen(s);
    int count = 0;
    for (int i = 0; i < n; i++) {
        count += s[i] != ('0' + (i & 1)) ? 0 : 1;
    }
    return min(count, n - count);
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
