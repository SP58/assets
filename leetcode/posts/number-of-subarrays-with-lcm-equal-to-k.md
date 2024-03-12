---
title: Number of Subarrays With LCM Equal to K
summary: Number of Subarrays With LCM Equal to K - Solution Explained
url: "/posts/number-of-subarrays-with-lcm-equal-to-k"
date: 2020-08-14T02:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Number of Subarrays With LCM Equal to K LeetCode Solution Explained in all languages", "2470", "leetcode question 2470", "Number of Subarrays With LCM Equal to K", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/number-of-subarrays-with-lcm-equal-to-k.webp
    alt: Number of Subarrays With LCM Equal to K - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2470. Number of Subarrays With LCM Equal to K](https://leetcode.com/problems/number-of-subarrays-with-lcm-equal-to-k)


## Description

<p>Given an integer array <code>nums</code> and an integer <code>k</code>, return <em>the number of <strong>subarrays</strong> of </em><code>nums</code><em> where the least common multiple of the subarray&#39;s elements is </em><code>k</code>.</p>

<p>A <strong>subarray</strong> is a contiguous non-empty sequence of elements within an array.</p>

<p>The <strong>least common multiple of an array</strong> is the smallest positive integer that is divisible by all the array elements.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,6,2,7,1], k = 6
<strong>Output:</strong> 4
<strong>Explanation:</strong> The subarrays of nums where 6 is the least common multiple of all the subarray&#39;s elements are:
- [<u><strong>3</strong></u>,<u><strong>6</strong></u>,2,7,1]
- [<u><strong>3</strong></u>,<u><strong>6</strong></u>,<u><strong>2</strong></u>,7,1]
- [3,<u><strong>6</strong></u>,2,7,1]
- [3,<u><strong>6</strong></u>,<u><strong>2</strong></u>,7,1]
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3], k = 2
<strong>Output:</strong> 0
<strong>Explanation:</strong> There are no subarrays of nums where 2 is the least common multiple of all the subarray&#39;s elements.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i], k &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1: Enumeration

Enumerate each number as the first number of the subarray, and then enumerate each number as the last number of the subarray. Calculate the least common multiple of this subarray. If the least common multiple equals $k$, then increment the answer by one.

The time complexity is $O(n^2)$. Here, $n$ is the length of the array.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def subarrayLCM(self, nums: List[int], k: int) -> int:
        n = len(nums)
        ans = 0
        for i in range(n):
            a = nums[i]
            for b in nums[i:]:
                x = lcm(a, b)
                ans += x == k
                a = x
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int subarrayLCM(int[] nums, int k) {
        int n = nums.length;
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            int a = nums[i];
            for (int j = i; j < n; ++j) {
                int b = nums[j];
                int x = lcm(a, b);
                if (x == k) {
                    ++ans;
                }
                a = x;
            }
        }
        return ans;
    }

    private int lcm(int a, int b) {
        return a * b / gcd(a, b);
    }

    private int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a % b);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int subarrayLCM(vector<int>& nums, int k) {
        int n = nums.size();
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            int a = nums[i];
            for (int j = i; j < n; ++j) {
                int b = nums[j];
                int x = lcm(a, b);
                ans += x == k;
                a = x;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func subarrayLCM(nums []int, k int) (ans int) {
	for i, a := range nums {
		for _, b := range nums[i:] {
			x := lcm(a, b)
			if x == k {
				ans++
			}
			a = x
		}
	}
	return
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}

func lcm(a, b int) int {
	return a * b / gcd(a, b)
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
