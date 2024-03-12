---
title: Binary Number with Alternating Bits
summary: Binary Number with Alternating Bits - Solution Explained
url: "/posts/binary-number-with-alternating-bits"
date: 2020-10-27T03:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Binary Number with Alternating Bits LeetCode Solution Explained in all languages", "693", "leetcode question 693", "Binary Number with Alternating Bits", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/binary-number-with-alternating-bits.webp
    alt: Binary Number with Alternating Bits - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [693. Binary Number with Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits)


## Description

<p>Given a positive integer, check whether it has alternating bits: namely, if two adjacent bits will always have different values.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 5
<strong>Output:</strong> true
<strong>Explanation:</strong> The binary representation of 5 is: 101
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 7
<strong>Output:</strong> false
<strong>Explanation:</strong> The binary representation of 7 is: 111.</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 11
<strong>Output:</strong> false
<strong>Explanation:</strong> The binary representation of 11 is: 1011.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def hasAlternatingBits(self, n: int) -> bool:
        prev = -1
        while n:
            curr = n & 1
            if prev == curr:
                return False
            prev = curr
            n >>= 1
        return True
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean hasAlternatingBits(int n) {
        int prev = -1;
        while (n != 0) {
            int curr = n & 1;
            if (prev == curr) {
                return false;
            }
            prev = curr;
            n >>= 1;
        }
        return true;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool hasAlternatingBits(int n) {
        int prev = -1;
        while (n) {
            int curr = n & 1;
            if (prev == curr) return false;
            prev = curr;
            n >>= 1;
        }
        return true;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func hasAlternatingBits(n int) bool {
	prev := -1
	for n != 0 {
		curr := n & 1
		if prev == curr {
			return false
		}
		prev = curr
		n >>= 1
	}
	return true
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn has_alternating_bits(mut n: i32) -> bool {
        let u = n & 3;
        if u != 1 && u != 2 {
            return false;
        }
        while n != 0 {
            if (n & 3) != u {
                return false;
            }
            n >>= 2;
        }
        true
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
    def hasAlternatingBits(self, n: int) -> bool:
        n ^= n >> 1
        return (n & (n + 1)) == 0
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean hasAlternatingBits(int n) {
        n ^= (n >> 1);
        return (n & (n + 1)) == 0;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool hasAlternatingBits(int n) {
        n ^= (n >> 1);
        return (n & ((long) n + 1)) == 0;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func hasAlternatingBits(n int) bool {
	n ^= (n >> 1)
	return (n & (n + 1)) == 0
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn has_alternating_bits(n: i32) -> bool {
        let t = n ^ (n >> 1);
        (t & (t + 1)) == 0
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
