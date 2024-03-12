---
title: Rotate String
summary: Rotate String - Solution Explained
url: "/posts/rotate-string"
date: 2020-10-22T20:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Rotate String LeetCode Solution Explained in all languages", "796", "leetcode question 796", "Rotate String", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/rotate-string.webp
    alt: Rotate String - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [796. Rotate String](https://leetcode.com/problems/rotate-string)


## Description

<p>Given two strings <code>s</code> and <code>goal</code>, return <code>true</code> <em>if and only if</em> <code>s</code> <em>can become</em> <code>goal</code> <em>after some number of <strong>shifts</strong> on</em> <code>s</code>.</p>

<p>A <strong>shift</strong> on <code>s</code> consists of moving the leftmost character of <code>s</code> to the rightmost position.</p>

<ul>
	<li>For example, if <code>s = &quot;abcde&quot;</code>, then it will be <code>&quot;bcdea&quot;</code> after one shift.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> s = "abcde", goal = "cdeab"
<strong>Output:</strong> true
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> s = "abcde", goal = "abced"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length, goal.length &lt;= 100</code></li>
	<li><code>s</code> and <code>goal</code> consist of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def rotateString(self, s: str, goal: str) -> bool:
        return len(s) == len(goal) and goal in s + s
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean rotateString(String s, String goal) {
        return s.length() == goal.length() && (s + s).contains(goal);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool rotateString(string s, string goal) {
        return s.size() == goal.size() && strstr((s + s).data(), goal.data());
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func rotateString(s string, goal string) bool {
	return len(s) == len(goal) && strings.Contains(s+s, goal)
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function rotateString(s: string, goal: string): boolean {
    return s.length === goal.length && (goal + goal).includes(s);
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn rotate_string(s: String, goal: String) -> bool {
        s.len() == goal.len() && (s.clone() + &s).contains(&goal)
    }
}
```
{{< /terminal >}}

{{< terminal title="PHP Code" >}}
```php
class Solution {
    /**
     * @param String $s
     * @param String $goal
     * @return Boolean
     */
    function rotateString($s, $goal) {
        return strlen($goal) === strlen($s) && strpos($s . $s, $goal) !== false;
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
