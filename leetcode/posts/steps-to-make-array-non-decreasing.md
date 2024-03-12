---
title: Steps to Make Array Non-decreasing
summary: Steps to Make Array Non-decreasing - Solution Explained
url: "/posts/steps-to-make-array-non-decreasing"
date: 2020-08-21T15:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Steps to Make Array Non-decreasing LeetCode Solution Explained in all languages", "2289", "leetcode question 2289", "Steps to Make Array Non-decreasing", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/steps-to-make-array-non-decreasing.webp
    alt: Steps to Make Array Non-decreasing - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2289. Steps to Make Array Non-decreasing](https://leetcode.com/problems/steps-to-make-array-non-decreasing)


## Description

<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code>. In one step, <strong>remove</strong> all elements <code>nums[i]</code> where <code>nums[i - 1] &gt; nums[i]</code> for all <code>0 &lt; i &lt; nums.length</code>.</p>

<p>Return <em>the number of steps performed until </em><code>nums</code><em> becomes a <strong>non-decreasing</strong> array</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,3,4,4,7,3,6,11,8,5,11]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The following are the steps performed:
- Step 1: [5,<strong><u>3</u></strong>,4,4,7,<u><strong>3</strong></u>,6,11,<u><strong>8</strong></u>,<u><strong>5</strong></u>,11] becomes [5,4,4,7,6,11,11]
- Step 2: [5,<u><strong>4</strong></u>,4,7,<u><strong>6</strong></u>,11,11] becomes [5,4,7,11,11]
- Step 3: [5,<u><strong>4</strong></u>,7,11,11] becomes [5,7,11,11]
[5,7,11,11] is a non-decreasing array. Therefore, we return 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,5,7,7,13]
<strong>Output:</strong> 0
<strong>Explanation:</strong> nums is already a non-decreasing array. Therefore, we return 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def totalSteps(self, nums: List[int]) -> int:
        stk = []
        ans, n = 0, len(nums)
        dp = [0] * n
        for i in range(n - 1, -1, -1):
            while stk and nums[i] > nums[stk[-1]]:
                dp[i] = max(dp[i] + 1, dp[stk.pop()])
            stk.append(i)
        return max(dp)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int totalSteps(int[] nums) {
        Deque<Integer> stk = new ArrayDeque<>();
        int ans = 0;
        int n = nums.length;
        int[] dp = new int[n];
        for (int i = n - 1; i >= 0; --i) {
            while (!stk.isEmpty() && nums[i] > nums[stk.peek()]) {
                dp[i] = Math.max(dp[i] + 1, dp[stk.pop()]);
                ans = Math.max(ans, dp[i]);
            }
            stk.push(i);
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
    int totalSteps(vector<int>& nums) {
        stack<int> stk;
        int ans = 0, n = nums.size();
        vector<int> dp(n);
        for (int i = n - 1; i >= 0; --i) {
            while (!stk.empty() && nums[i] > nums[stk.top()]) {
                dp[i] = max(dp[i] + 1, dp[stk.top()]);
                ans = max(ans, dp[i]);
                stk.pop();
            }
            stk.push(i);
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func totalSteps(nums []int) int {
	stk := []int{}
	ans, n := 0, len(nums)
	dp := make([]int, n)
	for i := n - 1; i >= 0; i-- {
		for len(stk) > 0 && nums[i] > nums[stk[len(stk)-1]] {
			dp[i] = max(dp[i]+1, dp[stk[len(stk)-1]])
			stk = stk[:len(stk)-1]
			ans = max(ans, dp[i])
		}
		stk = append(stk, i)
	}
	return ans
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function totalSteps(nums: number[]): number {
    let ans = 0;
    let stack = [];
    for (let num of nums) {
        let max = 0;
        while (stack.length && stack[0][0] <= num) {
            max = Math.max(stack[0][1], max);
            stack.shift();
        }
        if (stack.length) max++;
        ans = Math.max(max, ans);
        stack.unshift([num, max]);
    }
    return ans;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
