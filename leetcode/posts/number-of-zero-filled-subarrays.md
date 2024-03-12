---
title: Number of Zero-Filled Subarrays
summary: Number of Zero-Filled Subarrays - Solution Explained
url: "/posts/number-of-zero-filled-subarrays"
date: 2020-08-19T04:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Number of Zero-Filled Subarrays LeetCode Solution Explained in all languages", "2348", "leetcode question 2348", "Number of Zero-Filled Subarrays", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/number-of-zero-filled-subarrays.webp
    alt: Number of Zero-Filled Subarrays - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2348. Number of Zero-Filled Subarrays](https://leetcode.com/problems/number-of-zero-filled-subarrays)


## Description

<p>Given an integer array <code>nums</code>, return <em>the number of <strong>subarrays</strong> filled with </em><code>0</code>.</p>

<p>A <strong>subarray</strong> is a contiguous non-empty sequence of elements within an array.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,0,0,2,0,0,4]
<strong>Output:</strong> 6
<strong>Explanation:</strong> 
There are 4 occurrences of [0] as a subarray.
There are 2 occurrences of [0,0] as a subarray.
There is no occurrence of a subarray with a size more than 2 filled with 0. Therefore, we return 6.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,0,0,2,0,0]
<strong>Output:</strong> 9
<strong>Explanation:
</strong>There are 5 occurrences of [0] as a subarray.
There are 3 occurrences of [0,0] as a subarray.
There is 1 occurrence of [0,0,0] as a subarray.
There is no occurrence of a subarray with a size more than 3 filled with 0. Therefore, we return 9.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,10,2019]
<strong>Output:</strong> 0
<strong>Explanation:</strong> There is no subarray filled with 0. Therefore, we return 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def zeroFilledSubarray(self, nums: List[int]) -> int:
        ans = cnt = 0
        for v in nums:
            cnt = 0 if v else cnt + 1
            ans += cnt
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public long zeroFilledSubarray(int[] nums) {
        long ans = 0;
        int cnt = 0;
        for (int v : nums) {
            cnt = v != 0 ? 0 : cnt + 1;
            ans += cnt;
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
    long long zeroFilledSubarray(vector<int>& nums) {
        long long ans = 0;
        int cnt = 0;
        for (int& v : nums) {
            cnt = v ? 0 : cnt + 1;
            ans += cnt;
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func zeroFilledSubarray(nums []int) (ans int64) {
	cnt := 0
	for _, v := range nums {
		if v != 0 {
			cnt = 0
		} else {
			cnt++
		}
		ans += int64(cnt)
	}
	return
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function zeroFilledSubarray(nums: number[]): number {
    let ans = 0;
    let cnt = 0;
    for (const v of nums) {
        cnt = v ? 0 : cnt + 1;
        ans += cnt;
    }
    return ans;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
