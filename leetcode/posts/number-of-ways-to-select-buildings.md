---
title: Number of Ways to Select Buildings
summary: Number of Ways to Select Buildings - Solution Explained
url: "/posts/number-of-ways-to-select-buildings"
date: 2020-08-24T10:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Number of Ways to Select Buildings LeetCode Solution Explained in all languages", "2222", "leetcode question 2222", "Number of Ways to Select Buildings", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/number-of-ways-to-select-buildings.webp
    alt: Number of Ways to Select Buildings - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2222. Number of Ways to Select Buildings](https://leetcode.com/problems/number-of-ways-to-select-buildings)


## Description

<p>You are given a <strong>0-indexed</strong> binary string <code>s</code> which represents the types of buildings along a street where:</p>

<ul>
	<li><code>s[i] = &#39;0&#39;</code> denotes that the <code>i<sup>th</sup></code> building is an office and</li>
	<li><code>s[i] = &#39;1&#39;</code> denotes that the <code>i<sup>th</sup></code> building is a restaurant.</li>
</ul>

<p>As a city official, you would like to <strong>select</strong> 3 buildings for random inspection. However, to ensure variety, <strong>no two consecutive</strong> buildings out of the <strong>selected</strong> buildings can be of the same type.</p>

<ul>
	<li>For example, given <code>s = &quot;0<u><strong>0</strong></u>1<u><strong>1</strong></u>0<u><strong>1</strong></u>&quot;</code>, we cannot select the <code>1<sup>st</sup></code>, <code>3<sup>rd</sup></code>, and <code>5<sup>th</sup></code> buildings as that would form <code>&quot;0<strong><u>11</u></strong>&quot;</code> which is <strong>not</strong> allowed due to having two consecutive buildings of the same type.</li>
</ul>

<p>Return <em>the <b>number of valid ways</b> to select 3 buildings.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;001101&quot;
<strong>Output:</strong> 6
<strong>Explanation:</strong> 
The following sets of indices selected are valid:
- [0,2,4] from &quot;<u><strong>0</strong></u>0<strong><u>1</u></strong>1<strong><u>0</u></strong>1&quot; forms &quot;010&quot;
- [0,3,4] from &quot;<u><strong>0</strong></u>01<u><strong>10</strong></u>1&quot; forms &quot;010&quot;
- [1,2,4] from &quot;0<u><strong>01</strong></u>1<u><strong>0</strong></u>1&quot; forms &quot;010&quot;
- [1,3,4] from &quot;0<u><strong>0</strong></u>1<u><strong>10</strong></u>1&quot; forms &quot;010&quot;
- [2,4,5] from &quot;00<u><strong>1</strong></u>1<u><strong>01</strong></u>&quot; forms &quot;101&quot;
- [3,4,5] from &quot;001<u><strong>101</strong></u>&quot; forms &quot;101&quot;
No other selection is valid. Thus, there are 6 total ways.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;11100&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> It can be shown that there are no valid selections.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is either <code>&#39;0&#39;</code> or <code>&#39;1&#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def numberOfWays(self, s: str) -> int:
        n = len(s)
        cnt0 = s.count("0")
        cnt1 = n - cnt0
        c0 = c1 = 0
        ans = 0
        for c in s:
            if c == "0":
                ans += c1 * (cnt1 - c1)
                c0 += 1
            else:
                ans += c0 * (cnt0 - c0)
                c1 += 1
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public long numberOfWays(String s) {
        int n = s.length();
        int cnt0 = 0;
        for (char c : s.toCharArray()) {
            if (c == '0') {
                ++cnt0;
            }
        }
        int cnt1 = n - cnt0;
        long ans = 0;
        int c0 = 0, c1 = 0;
        for (char c : s.toCharArray()) {
            if (c == '0') {
                ans += c1 * (cnt1 - c1);
                ++c0;
            } else {
                ans += c0 * (cnt0 - c0);
                ++c1;
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
    long long numberOfWays(string s) {
        int n = s.size();
        int cnt0 = 0;
        for (char& c : s) cnt0 += c == '0';
        int cnt1 = n - cnt0;
        int c0 = 0, c1 = 0;
        long long ans = 0;
        for (char& c : s) {
            if (c == '0') {
                ans += c1 * (cnt1 - c1);
                ++c0;
            } else {
                ans += c0 * (cnt0 - c0);
                ++c1;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func numberOfWays(s string) int64 {
	n := len(s)
	cnt0 := strings.Count(s, "0")
	cnt1 := n - cnt0
	c0, c1 := 0, 0
	ans := 0
	for _, c := range s {
		if c == '0' {
			ans += c1 * (cnt1 - c1)
			c0++
		} else {
			ans += c0 * (cnt0 - c0)
			c1++
		}
	}
	return int64(ans)
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
