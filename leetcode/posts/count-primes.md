---
title: Count Primes
summary: Count Primes - Solution Explained
url: "/posts/count-primes"
date: 2020-11-16T12:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Count Primes LeetCode Solution Explained in all languages", "204", "leetcode question 204", "Count Primes", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/count-primes.webp
    alt: Count Primes - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [204. Count Primes](https://leetcode.com/problems/count-primes)


## Description

<p>Given an integer <code>n</code>, return <em>the number of prime numbers that are strictly less than</em> <code>n</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 0
<strong>Output:</strong> 0
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 5 * 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def countPrimes(self, n: int) -> int:
        primes = [True] * n
        ans = 0
        for i in range(2, n):
            if primes[i]:
                ans += 1
                for j in range(i + i, n, i):
                    primes[j] = False
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int countPrimes(int n) {
        boolean[] primes = new boolean[n];
        Arrays.fill(primes, true);
        int ans = 0;
        for (int i = 2; i < n; ++i) {
            if (primes[i]) {
                ++ans;
                for (int j = i + i; j < n; j += i) {
                    primes[j] = false;
                }
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
    int countPrimes(int n) {
        vector<bool> primes(n, true);
        int ans = 0;
        for (int i = 2; i < n; ++i) {
            if (primes[i]) {
                ++ans;
                for (int j = i; j < n; j += i) primes[j] = false;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func countPrimes(n int) int {
	primes := make([]bool, n)
	for i := range primes {
		primes[i] = true
	}
	ans := 0
	for i := 2; i < n; i++ {
		if primes[i] {
			ans++
			for j := i + i; j < n; j += i {
				primes[j] = false
			}
		}
	}
	return ans
}
```
{{< /terminal >}}

{{< terminal title="JavaScript Code" >}}
```js
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function (n) {
    let primes = new Array(n).fill(true);
    let ans = 0;
    for (let i = 2; i < n; ++i) {
        if (primes[i]) {
            ++ans;
            for (let j = i + i; j < n; j += i) {
                primes[j] = false;
            }
        }
    }
    return ans;
};
```
{{< /terminal >}}

{{< terminal title="C# Code" >}}
```cs
public class Solution {
    public int CountPrimes(int n) {
        var notPrimes = new bool[n];
        int ans = 0;
        for (int i = 2; i < n; ++i)
        {
            if (!notPrimes[i])
            {
                ++ans;
                for (int j = i + i; j < n; j += i)
                {
                    notPrimes[j] = true;
                }
            }
        }
        return ans;
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
