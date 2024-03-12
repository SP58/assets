---
title: Divide Array Into Equal Pairs
summary: Divide Array Into Equal Pairs - Solution Explained
url: "/posts/divide-array-into-equal-pairs"
date: 2020-08-25T02:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Divide Array Into Equal Pairs LeetCode Solution Explained in all languages", "2206", "leetcode question 2206", "Divide Array Into Equal Pairs", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/divide-array-into-equal-pairs.webp
    alt: Divide Array Into Equal Pairs - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2206. Divide Array Into Equal Pairs](https://leetcode.com/problems/divide-array-into-equal-pairs)


## Description

<p>You are given an integer array <code>nums</code> consisting of <code>2 * n</code> integers.</p>

<p>You need to divide <code>nums</code> into <code>n</code> pairs such that:</p>

<ul>
	<li>Each element belongs to <strong>exactly one</strong> pair.</li>
	<li>The elements present in a pair are <strong>equal</strong>.</li>
</ul>

<p>Return <code>true</code> <em>if nums can be divided into</em> <code>n</code> <em>pairs, otherwise return</em> <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,2,3,2,2,2]
<strong>Output:</strong> true
<strong>Explanation:</strong> 
There are 6 elements in nums, so they should be divided into 6 / 2 = 3 pairs.
If nums is divided into the pairs (2, 2), (3, 3), and (2, 2), it will satisfy all the conditions.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4]
<strong>Output:</strong> false
<strong>Explanation:</strong> 
There is no way to divide nums into 4 / 2 = 2 pairs such that the pairs satisfy every condition.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>nums.length == 2 * n</code></li>
	<li><code>1 &lt;= n &lt;= 500</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 500</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def divideArray(self, nums: List[int]) -> bool:
        cnt = Counter(nums)
        return all(v % 2 == 0 for v in cnt.values())
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean divideArray(int[] nums) {
        int[] cnt = new int[510];
        for (int v : nums) {
            ++cnt[v];
        }
        for (int v : cnt) {
            if (v % 2 != 0) {
                return false;
            }
        }
        return true;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool divideArray(vector<int>& nums) {
        vector<int> cnt(510);
        for (int& v : nums) ++cnt[v];
        for (int& v : cnt)
            if (v % 2)
                return false;
        return true;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func divideArray(nums []int) bool {
	cnt := make([]int, 510)
	for _, v := range nums {
		cnt[v]++
	}
	for _, v := range cnt {
		if v%2 == 1 {
			return false
		}
	}
	return true
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
