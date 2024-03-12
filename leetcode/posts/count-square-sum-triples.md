---
title: Count Square Sum Triples
summary: Count Square Sum Triples - Solution Explained
url: "/posts/count-square-sum-triples"
date: 2020-09-05T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Count Square Sum Triples LeetCode Solution Explained in all languages", "1925", "leetcode question 1925", "Count Square Sum Triples", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/count-square-sum-triples.webp
    alt: Count Square Sum Triples - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1925. Count Square Sum Triples](https://leetcode.com/problems/count-square-sum-triples)


## Description

<p>A <strong>square triple</strong> <code>(a,b,c)</code> is a triple where <code>a</code>, <code>b</code>, and <code>c</code> are <strong>integers</strong> and <code>a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup></code>.</p>

<p>Given an integer <code>n</code>, return <em>the number of <strong>square triples</strong> such that </em><code>1 &lt;= a, b, c &lt;= n</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 5
<strong>Output:</strong> 2
<strong>Explanation</strong>: The square triples are (3,4,5) and (4,3,5).
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> 4
<strong>Explanation</strong>: The square triples are (3,4,5), (4,3,5), (6,8,10), and (8,6,10).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 250</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def countTriples(self, n: int) -> int:
        res = 0
        for a in range(1, n + 1):
            for b in range(1, n + 1):
                t = a**2 + b**2
                c = int(sqrt(t))
                if c <= n and c**2 == t:
                    res += 1
        return res
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int countTriples(int n) {
        int res = 0;
        for (int a = 1; a <= n; ++a) {
            for (int b = 1; b <= n; ++b) {
                int t = a * a + b * b;
                int c = (int) Math.sqrt(t);
                if (c <= n && c * c == t) {
                    ++res;
                }
            }
        }
        return res;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int countTriples(int n) {
        int res = 0;
        for (int a = 1; a <= n; ++a) {
            for (int b = 1; b <= n; ++b) {
                int t = a * a + b * b;
                int c = (int) sqrt(t);
                if (c <= n && c * c == t) {
                    ++res;
                }
            }
        }
        return res;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func countTriples(n int) int {
	res := 0
	for a := 1; a <= n; a++ {
		for b := 1; b <= n; b++ {
			t := a*a + b*b
			c := int(math.Sqrt(float64(t)))
			if c <= n && c*c == t {
				res++
			}
		}
	}
	return res
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
