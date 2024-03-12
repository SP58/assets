---
title: Prime Number of Set Bits in Binary Representation
summary: Prime Number of Set Bits in Binary Representation - Solution Explained
url: "/posts/prime-number-of-set-bits-in-binary-representation"
date: 2020-10-24T06:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Prime Number of Set Bits in Binary Representation LeetCode Solution Explained in all languages", "762", "leetcode question 762", "Prime Number of Set Bits in Binary Representation", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/prime-number-of-set-bits-in-binary-representation.webp
    alt: Prime Number of Set Bits in Binary Representation - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [762. Prime Number of Set Bits in Binary Representation](https://leetcode.com/problems/prime-number-of-set-bits-in-binary-representation)


## Description

<p>Given two integers <code>left</code> and <code>right</code>, return <em>the <strong>count</strong> of numbers in the <strong>inclusive</strong> range </em><code>[left, right]</code><em> having a <strong>prime number of set bits</strong> in their binary representation</em>.</p>

<p>Recall that the <strong>number of set bits</strong> an integer has is the number of <code>1</code>&#39;s present when written in binary.</p>

<ul>
	<li>For example, <code>21</code> written in binary is <code>10101</code>, which has <code>3</code> set bits.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> left = 6, right = 10
<strong>Output:</strong> 4
<strong>Explanation:</strong>
6  -&gt; 110 (2 set bits, 2 is prime)
7  -&gt; 111 (3 set bits, 3 is prime)
8  -&gt; 1000 (1 set bit, 1 is not prime)
9  -&gt; 1001 (2 set bits, 2 is prime)
10 -&gt; 1010 (2 set bits, 2 is prime)
4 numbers have a prime number of set bits.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> left = 10, right = 15
<strong>Output:</strong> 5
<strong>Explanation:</strong>
10 -&gt; 1010 (2 set bits, 2 is prime)
11 -&gt; 1011 (3 set bits, 3 is prime)
12 -&gt; 1100 (2 set bits, 2 is prime)
13 -&gt; 1101 (3 set bits, 3 is prime)
14 -&gt; 1110 (3 set bits, 3 is prime)
15 -&gt; 1111 (4 set bits, 4 is not prime)
5 numbers have a prime number of set bits.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= left &lt;= right &lt;= 10<sup>6</sup></code></li>
	<li><code>0 &lt;= right - left &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def countPrimeSetBits(self, left: int, right: int) -> int:
        primes = {2, 3, 5, 7, 11, 13, 17, 19}
        return sum(i.bit_count() in primes for i in range(left, right + 1))
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    private static Set<Integer> primes = Set.of(2, 3, 5, 7, 11, 13, 17, 19);

    public int countPrimeSetBits(int left, int right) {
        int ans = 0;
        for (int i = left; i <= right; ++i) {
            if (primes.contains(Integer.bitCount(i))) {
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
    int countPrimeSetBits(int left, int right) {
        unordered_set<int> primes{2, 3, 5, 7, 11, 13, 17, 19};
        int ans = 0;
        for (int i = left; i <= right; ++i) ans += primes.count(__builtin_popcount(i));
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func countPrimeSetBits(left int, right int) (ans int) {
	primes := map[int]int{}
	for _, v := range []int{2, 3, 5, 7, 11, 13, 17, 19} {
		primes[v] = 1
	}
	for i := left; i <= right; i++ {
		ans += primes[bits.OnesCount(uint(i))]
	}
	return
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
