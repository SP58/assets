---
title: Longest Substring with At Most Two Distinct Characters
summary: Longest Substring with At Most Two Distinct Characters - Solution Explained
url: "/posts/longest-substring-with-at-most-two-distinct-characters"
date: 2020-11-18T09:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Longest Substring with At Most Two Distinct Characters LeetCode Solution Explained in all languages", "159", "leetcode question 159", "Longest Substring with At Most Two Distinct Characters", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/longest-substring-with-at-most-two-distinct-characters.webp
    alt: Longest Substring with At Most Two Distinct Characters - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [159. Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters)


## Description

<p>Given a string <code>s</code>, return <em>the length of the longest </em><span data-keyword="substring-nonempty"><em>substring</em></span><em> that contains at most <strong>two distinct characters</strong></em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;eceba&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> The substring is &quot;ece&quot; which its length is 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ccaabbb&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The substring is &quot;aabbb&quot; which its length is 5.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def lengthOfLongestSubstringTwoDistinct(self, s: str) -> int:
        cnt = Counter()
        ans = j = 0
        for i, c in enumerate(s):
            cnt[c] += 1
            while len(cnt) > 2:
                cnt[s[j]] -= 1
                if cnt[s[j]] == 0:
                    cnt.pop(s[j])
                j += 1
            ans = max(ans, i - j + 1)
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int lengthOfLongestSubstringTwoDistinct(String s) {
        Map<Character, Integer> cnt = new HashMap<>();
        int n = s.length();
        int ans = 0;
        for (int i = 0, j = 0; i < n; ++i) {
            char c = s.charAt(i);
            cnt.put(c, cnt.getOrDefault(c, 0) + 1);
            while (cnt.size() > 2) {
                char t = s.charAt(j++);
                cnt.put(t, cnt.get(t) - 1);
                if (cnt.get(t) == 0) {
                    cnt.remove(t);
                }
            }
            ans = Math.max(ans, i - j + 1);
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
    int lengthOfLongestSubstringTwoDistinct(string s) {
        unordered_map<char, int> cnt;
        int n = s.size();
        int ans = 0;
        for (int i = 0, j = 0; i < n; ++i) {
            cnt[s[i]]++;
            while (cnt.size() > 2) {
                cnt[s[j]]--;
                if (cnt[s[j]] == 0) {
                    cnt.erase(s[j]);
                }
                ++j;
            }
            ans = max(ans, i - j + 1);
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func lengthOfLongestSubstringTwoDistinct(s string) (ans int) {
	cnt := map[byte]int{}
	j := 0
	for i := range s {
		cnt[s[i]]++
		for len(cnt) > 2 {
			cnt[s[j]]--
			if cnt[s[j]] == 0 {
				delete(cnt, s[j])
			}
			j++
		}
		ans = max(ans, i-j+1)
	}
	return
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
