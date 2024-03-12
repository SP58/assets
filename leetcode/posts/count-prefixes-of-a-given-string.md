---
title: Count Prefixes of a Given String
summary: Count Prefixes of a Given String - Solution Explained
url: "/posts/count-prefixes-of-a-given-string"
date: 2020-08-23T01:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Count Prefixes of a Given String LeetCode Solution Explained in all languages", "2255", "leetcode question 2255", "Count Prefixes of a Given String", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/count-prefixes-of-a-given-string.webp
    alt: Count Prefixes of a Given String - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2255. Count Prefixes of a Given String](https://leetcode.com/problems/count-prefixes-of-a-given-string)


## Description

<p>You are given a string array <code>words</code> and a string <code>s</code>, where <code>words[i]</code> and <code>s</code> comprise only of <strong>lowercase English letters</strong>.</p>

<p>Return <em>the <strong>number of strings</strong> in</em> <code>words</code> <em>that are a <strong>prefix</strong> of</em> <code>s</code>.</p>

<p>A <strong>prefix</strong> of a string is a substring that occurs at the beginning of the string. A <b>substring</b> is a contiguous sequence of characters within a string.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;a&quot;,&quot;b&quot;,&quot;c&quot;,&quot;ab&quot;,&quot;bc&quot;,&quot;abc&quot;], s = &quot;abc&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong>
The strings in words which are a prefix of s = &quot;abc&quot; are:
&quot;a&quot;, &quot;ab&quot;, and &quot;abc&quot;.
Thus the number of strings in words which are a prefix of s is 3.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;a&quot;,&quot;a&quot;], s = &quot;aa&quot;
<strong>Output:</strong> 2
<strong>Explanation:
</strong>Both of the strings are a prefix of s. 
Note that the same string can occur multiple times in words, and it should be counted each time.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 1000</code></li>
	<li><code>1 &lt;= words[i].length, s.length &lt;= 10</code></li>
	<li><code>words[i]</code> and <code>s</code> consist of lowercase English letters <strong>only</strong>.</li>
</ul>

## Solutions

### Solution 1: Traversal Counting

We directly traverse the array words, and for each string w, we check if s starts with w as a prefix. If it does, we increment the answer by one.

After the traversal, we return the answer.

The time complexity is $O(m \times n)$, where $m$ and $n$ are the lengths of the array words and the string s, respectively. The space complexity is $O(1)$.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def countPrefixes(self, words: List[str], s: str) -> int:
        return sum(s.startswith(w) for w in words)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int countPrefixes(String[] words, String s) {
        int ans = 0;
        for (String w : words) {
            if (s.startsWith(w)) {
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
    int countPrefixes(vector<string>& words, string s) {
        int ans = 0;
        for (auto& w : words) {
            ans += s.starts_with(w);
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func countPrefixes(words []string, s string) (ans int) {
	for _, w := range words {
		if strings.HasPrefix(s, w) {
			ans++
		}
	}
	return
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function countPrefixes(words: string[], s: string): number {
    return words.filter(w => s.startsWith(w)).length;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
