---
title: Sum of Subsequence Widths
summary: Sum of Subsequence Widths - Solution Explained
url: "/posts/sum-of-subsequence-widths"
date: 2020-10-18T21:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Sum of Subsequence Widths LeetCode Solution Explained in all languages", "891", "leetcode question 891", "Sum of Subsequence Widths", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/sum-of-subsequence-widths.webp
    alt: Sum of Subsequence Widths - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [891. Sum of Subsequence Widths](https://leetcode.com/problems/sum-of-subsequence-widths)


## Description

<p>The <strong>width</strong> of a sequence is the difference between the maximum and minimum elements in the sequence.</p>

<p>Given an array of integers <code>nums</code>, return <em>the sum of the <strong>widths</strong> of all the non-empty <strong>subsequences</strong> of </em><code>nums</code>. Since the answer may be very large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>A <strong>subsequence</strong> is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, <code>[3,6,2,7]</code> is a subsequence of the array <code>[0,3,1,6,2,2,7]</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,3]
<strong>Output:</strong> 6
Explanation: The subsequences are [1], [2], [3], [2,1], [2,3], [1,3], [2,1,3].
The corresponding widths are 0, 0, 0, 1, 1, 2, 2.
The sum of these widths is 6.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def sumSubseqWidths(self, nums: List[int]) -> int:
        mod = 10**9 + 7
        nums.sort()
        ans, p = 0, 1
        for i, v in enumerate(nums):
            ans = (ans + (v - nums[-i - 1]) * p) % mod
            p = (p << 1) % mod
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    private static final int MOD = (int) 1e9 + 7;

    public int sumSubseqWidths(int[] nums) {
        Arrays.sort(nums);
        long ans = 0, p = 1;
        int n = nums.length;
        for (int i = 0; i < n; ++i) {
            ans = (ans + (nums[i] - nums[n - i - 1]) * p + MOD) % MOD;
            p = (p << 1) % MOD;
        }
        return (int) ans;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    const int mod = 1e9 + 7;

    int sumSubseqWidths(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        long ans = 0, p = 1;
        int n = nums.size();
        for (int i = 0; i < n; ++i) {
            ans = (ans + (nums[i] - nums[n - i - 1]) * p + mod) % mod;
            p = (p << 1) % mod;
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func sumSubseqWidths(nums []int) (ans int) {
	const mod int = 1e9 + 7
	sort.Ints(nums)
	p, n := 1, len(nums)
	for i, v := range nums {
		ans = (ans + (v-nums[n-i-1])*p + mod) % mod
		p = (p << 1) % mod
	}
	return
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
