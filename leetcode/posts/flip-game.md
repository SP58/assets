---
title: Flip Game
summary: Flip Game - Solution Explained
url: "/posts/flip-game"
date: 2020-11-12T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Flip Game LeetCode Solution Explained in all languages", "293", "leetcode question 293", "Flip Game", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/flip-game.webp
    alt: Flip Game - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [293. Flip Game](https://leetcode.com/problems/flip-game)


## Description

<p>You are playing a Flip Game with your friend.</p>

<p>You are given a string <code>currentState</code> that contains only <code>&#39;+&#39;</code> and <code>&#39;-&#39;</code>. You and your friend take turns to flip <strong>two consecutive</strong> <code>&quot;++&quot;</code> into <code>&quot;--&quot;</code>. The game ends when a person can no longer make a move, and therefore the other person will be the winner.</p>

<p>Return all possible states of the string <code>currentState</code> after <strong>one valid move</strong>. You may return the answer in <strong>any order</strong>. If there is no valid move, return an empty list <code>[]</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> currentState = &quot;++++&quot;
<strong>Output:</strong> [&quot;--++&quot;,&quot;+--+&quot;,&quot;++--&quot;]
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> currentState = &quot;+&quot;
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= currentState.length &lt;= 500</code></li>
	<li><code>currentState[i]</code> is either <code>&#39;+&#39;</code> or <code>&#39;-&#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def generatePossibleNextMoves(self, currentState: str) -> List[str]:
        s = list(currentState)
        ans = []
        for i, c in enumerate(s[:-1]):
            if c == "+" and s[i + 1] == "+":
                s[i] = s[i + 1] = "-"
                ans.append("".join(s))
                s[i] = s[i + 1] = "+"
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public List<String> generatePossibleNextMoves(String currentState) {
        char[] cs = currentState.toCharArray();
        List<String> ans = new ArrayList<>();
        for (int i = 0; i < cs.length - 1; ++i) {
            if (cs[i] == '+' && cs[i + 1] == '+') {
                cs[i] = '-';
                cs[i + 1] = '-';
                ans.add(String.valueOf(cs));
                cs[i] = '+';
                cs[i + 1] = '+';
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
    vector<string> generatePossibleNextMoves(string currentState) {
        vector<string> ans;
        for (int i = 0; i < currentState.size() - 1; ++i) {
            if (currentState[i] == '+' && currentState[i + 1] == '+') {
                currentState[i] = '-';
                currentState[i + 1] = '-';
                ans.push_back(currentState);
                currentState[i] = '+';
                currentState[i + 1] = '+';
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func generatePossibleNextMoves(currentState string) []string {
	ans := []string{}
	cs := []byte(currentState)
	for i, c := range cs[1:] {
		if c == '+' && cs[i] == '+' {
			cs[i], cs[i+1] = '-', '-'
			ans = append(ans, string(cs))
			cs[i], cs[i+1] = '+', '+'
		}
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
