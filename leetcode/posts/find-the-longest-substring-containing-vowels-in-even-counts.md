---
title: Find the Longest Substring Containing Vowels in Even Counts
summary: Find the Longest Substring Containing Vowels in Even Counts - Solution Explained
url: "/posts/find-the-longest-substring-containing-vowels-in-even-counts"
date: 2020-09-28T21:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Find the Longest Substring Containing Vowels in Even Counts LeetCode Solution Explained in all languages", "1371", "leetcode question 1371", "Find the Longest Substring Containing Vowels in Even Counts", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/find-the-longest-substring-containing-vowels-in-even-counts.webp
    alt: Find the Longest Substring Containing Vowels in Even Counts - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1371. Find the Longest Substring Containing Vowels in Even Counts](https://leetcode.com/problems/find-the-longest-substring-containing-vowels-in-even-counts)


## Description

<p>Given the string <code>s</code>, return the size of the longest substring containing each vowel an even number of times. That is, &#39;a&#39;, &#39;e&#39;, &#39;i&#39;, &#39;o&#39;, and &#39;u&#39; must appear an even number of times.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;eleetminicoworoep&quot;
<strong>Output:</strong> 13
<strong>Explanation: </strong>The longest substring is &quot;leetminicowor&quot; which contains two each of the vowels: <strong>e</strong>, <strong>i</strong> and <strong>o</strong> and zero of the vowels: <strong>a</strong> and <strong>u</strong>.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcodeisgreat&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The longest substring is &quot;leetc&quot; which contains two e&#39;s.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bcbcbc&quot;
<strong>Output:</strong> 6
<strong>Explanation:</strong> In this case, the given string &quot;bcbcbc&quot; is the longest because all vowels: <strong>a</strong>, <strong>e</strong>, <strong>i</strong>, <strong>o</strong> and <strong>u</strong> appear zero times.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 x 10^5</code></li>
	<li><code>s</code>&nbsp;contains only lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def findTheLongestSubstring(self, s: str) -> int:
        pos = [inf] * 32
        pos[0] = -1
        vowels = 'aeiou'
        state = ans = 0
        for i, c in enumerate(s):
            for j, v in enumerate(vowels):
                if c == v:
                    state ^= 1 << j
            ans = max(ans, i - pos[state])
            pos[state] = min(pos[state], i)
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {

    public int findTheLongestSubstring(String s) {
        int[] pos = new int[32];
        Arrays.fill(pos, Integer.MAX_VALUE);
        pos[0] = -1;
        String vowels = "aeiou";
        int state = 0;
        int ans = 0;
        for (int i = 0; i < s.length(); ++i) {
            char c = s.charAt(i);
            for (int j = 0; j < 5; ++j) {
                if (c == vowels.charAt(j)) {
                    state ^= (1 << j);
                }
            }
            ans = Math.max(ans, i - pos[state]);
            pos[state] = Math.min(pos[state], i);
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
    int findTheLongestSubstring(string s) {
        vector<int> pos(32, INT_MAX);
        pos[0] = -1;
        string vowels = "aeiou";
        int state = 0, ans = 0;
        for (int i = 0; i < s.size(); ++i) {
            for (int j = 0; j < 5; ++j)
                if (s[i] == vowels[j])
                    state ^= (1 << j);
            ans = max(ans, i - pos[state]);
            pos[state] = min(pos[state], i);
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func findTheLongestSubstring(s string) int {
	pos := make([]int, 32)
	for i := range pos {
		pos[i] = math.MaxInt32
	}
	pos[0] = -1
	vowels := "aeiou"
	state, ans := 0, 0
	for i, c := range s {
		for j, v := range vowels {
			if c == v {
				state ^= (1 << j)
			}
		}
		ans = max(ans, i-pos[state])
		pos[state] = min(pos[state], i)
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
