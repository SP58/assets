---
title: Reordered Power of 2
summary: Reordered Power of 2 - Solution Explained
url: "/posts/reordered-power-of-2"
date: 2020-10-19T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Reordered Power of 2 LeetCode Solution Explained in all languages", "869", "leetcode question 869", "Reordered Power of 2", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/reordered-power-of-2.webp
    alt: Reordered Power of 2 - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [869. Reordered Power of 2](https://leetcode.com/problems/reordered-power-of-2)


## Description

<p>You are given an integer <code>n</code>. We reorder the digits in any order (including the original order) such that the leading digit is not zero.</p>

<p>Return <code>true</code> <em>if and only if we can do this so that the resulting number is a power of two</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> true
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def reorderedPowerOf2(self, n: int) -> bool:
        def convert(n):
            cnt = [0] * 10
            while n:
                n, v = divmod(n, 10)
                cnt[v] += 1
            return cnt

        i, s = 1, convert(n)
        while i <= 10**9:
            if convert(i) == s:
                return True
            i <<= 1
        return False
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean reorderedPowerOf2(int n) {
        String s = convert(n);
        for (int i = 1; i <= Math.pow(10, 9); i <<= 1) {
            if (s.equals(convert(i))) {
                return true;
            }
        }
        return false;
    }

    private String convert(int n) {
        char[] cnt = new char[10];
        for (; n > 0; n /= 10) {
            cnt[n % 10]++;
        }
        return new String(cnt);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool reorderedPowerOf2(int n) {
        vector<int> s = convert(n);
        for (int i = 1; i <= pow(10, 9); i <<= 1)
            if (s == convert(i))
                return true;
        return false;
    }

    vector<int> convert(int n) {
        vector<int> cnt(10);
        for (; n; n /= 10) ++cnt[n % 10];
        return cnt;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func reorderedPowerOf2(n int) bool {
	convert := func(n int) []byte {
		cnt := make([]byte, 10)
		for ; n > 0; n /= 10 {
			cnt[n%10]++
		}
		return cnt
	}
	s := convert(n)
	for i := 1; i <= 1e9; i <<= 1 {
		if bytes.Equal(s, convert(i)) {
			return true
		}
	}
	return false
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
