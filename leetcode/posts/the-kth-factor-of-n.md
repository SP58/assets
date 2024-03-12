---
title: The kth Factor of n
summary: The kth Factor of n - Solution Explained
url: "/posts/the-kth-factor-of-n"
date: 2020-09-23T20:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["The kth Factor of n LeetCode Solution Explained in all languages", "1492", "leetcode question 1492", "The kth Factor of n", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/the-kth-factor-of-n.webp
    alt: The kth Factor of n - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1492. The kth Factor of n](https://leetcode.com/problems/the-kth-factor-of-n)


## Description

<p>You are given two positive integers <code>n</code> and <code>k</code>. A factor of an integer <code>n</code> is defined as an integer <code>i</code> where <code>n % i == 0</code>.</p>

<p>Consider a list of all factors of <code>n</code> sorted in <strong>ascending order</strong>, return <em>the </em><code>k<sup>th</sup></code><em> factor</em> in this list or return <code>-1</code> if <code>n</code> has less than <code>k</code> factors.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 12, k = 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> Factors list is [1, 2, 3, 4, 6, 12], the 3<sup>rd</sup> factor is 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 7, k = 2
<strong>Output:</strong> 7
<strong>Explanation:</strong> Factors list is [1, 7], the 2<sup>nd</sup> factor is 7.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 4, k = 4
<strong>Output:</strong> -1
<strong>Explanation:</strong> Factors list is [1, 2, 4], there is only 3 factors. We should return -1.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= n &lt;= 1000</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<p>Could you solve this problem in less than O(n) complexity?</p>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def kthFactor(self, n: int, k: int) -> int:
        for i in range(1, n + 1):
            if n % i == 0:
                k -= 1
                if k == 0:
                    return i
        return -1
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int kthFactor(int n, int k) {
        for (int i = 1; i <= n; ++i) {
            if (n % i == 0 && (--k == 0)) {
                return i;
            }
        }
        return -1;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int kthFactor(int n, int k) {
        int i = 1;
        for (; i < n / i; ++i) {
            if (n % i == 0 && (--k == 0)) {
                return i;
            }
        }
        if (i * i != n) {
            --i;
        }
        for (; i > 0; --i) {
            if (n % (n / i) == 0 && (--k == 0)) {
                return n / i;
            }
        }
        return -1;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func kthFactor(n int, k int) int {
	for i := 1; i <= n; i++ {
		if n%i == 0 {
			k--
			if k == 0 {
				return i
			}
		}
	}
	return -1
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def kthFactor(self, n: int, k: int) -> int:
        i = 1
        while i * i < n:
            if n % i == 0:
                k -= 1
                if k == 0:
                    return i
            i += 1
        if i * i != n:
            i -= 1
        while i:
            if (n % (n // i)) == 0:
                k -= 1
                if k == 0:
                    return n // i
            i -= 1
        return -1
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int kthFactor(int n, int k) {
        int i = 1;
        for (; i < n / i; ++i) {
            if (n % i == 0 && (--k == 0)) {
                return i;
            }
        }
        if (i * i != n) {
            --i;
        }
        for (; i > 0; --i) {
            if (n % (n / i) == 0 && (--k == 0)) {
                return n / i;
            }
        }
        return -1;
    }
}
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func kthFactor(n int, k int) int {
	i := 1
	for ; i < n/i; i++ {
		if n%i == 0 {
			k--
			if k == 0 {
				return i
			}
		}
	}
	if i*i != n {
		i--
	}
	for ; i > 0; i-- {
		if n%(n/i) == 0 {
			k--
			if k == 0 {
				return n / i
			}
		}
	}
	return -1
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
