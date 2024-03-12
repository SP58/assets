---
title: Partition Array Such That Maximum Difference Is K
summary: Partition Array Such That Maximum Difference Is K - Solution Explained
url: "/posts/partition-array-such-that-maximum-difference-is-k"
date: 2020-08-21T10:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Partition Array Such That Maximum Difference Is K LeetCode Solution Explained in all languages", "2294", "leetcode question 2294", "Partition Array Such That Maximum Difference Is K", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/partition-array-such-that-maximum-difference-is-k.webp
    alt: Partition Array Such That Maximum Difference Is K - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2294. Partition Array Such That Maximum Difference Is K](https://leetcode.com/problems/partition-array-such-that-maximum-difference-is-k)


## Description

<p>You are given an integer array <code>nums</code> and an integer <code>k</code>. You may partition <code>nums</code> into one or more <strong>subsequences</strong> such that each element in <code>nums</code> appears in <strong>exactly</strong> one of the subsequences.</p>

<p>Return <em>the <strong>minimum </strong>number of subsequences needed such that the difference between the maximum and minimum values in each subsequence is <strong>at most</strong> </em><code>k</code><em>.</em></p>

<p>A <strong>subsequence</strong> is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,6,1,2,5], k = 2
<strong>Output:</strong> 2
<strong>Explanation:</strong>
We can partition nums into the two subsequences [3,1,2] and [6,5].
The difference between the maximum and minimum value in the first subsequence is 3 - 1 = 2.
The difference between the maximum and minimum value in the second subsequence is 6 - 5 = 1.
Since two subsequences were created, we return 2. It can be shown that 2 is the minimum number of subsequences needed.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3], k = 1
<strong>Output:</strong> 2
<strong>Explanation:</strong>
We can partition nums into the two subsequences [1,2] and [3].
The difference between the maximum and minimum value in the first subsequence is 2 - 1 = 1.
The difference between the maximum and minimum value in the second subsequence is 3 - 3 = 0.
Since two subsequences were created, we return 2. Note that another optimal solution is to partition nums into the two subsequences [1] and [2,3].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,2,4,5], k = 0
<strong>Output:</strong> 3
<strong>Explanation:</strong>
We can partition nums into the three subsequences [2,2], [4], and [5].
The difference between the maximum and minimum value in the first subsequences is 2 - 2 = 0.
The difference between the maximum and minimum value in the second subsequences is 4 - 4 = 0.
The difference between the maximum and minimum value in the third subsequences is 5 - 5 = 0.
Since three subsequences were created, we return 3. It can be shown that 3 is the minimum number of subsequences needed.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def partitionArray(self, nums: List[int], k: int) -> int:
        nums.sort()
        ans, a = 1, nums[0]
        for b in nums:
            if b - a > k:
                a = b
                ans += 1
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int partitionArray(int[] nums, int k) {
        Arrays.sort(nums);
        int ans = 1, a = nums[0];
        for (int b : nums) {
            if (b - a > k) {
                a = b;
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
    int partitionArray(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        int ans = 1, a = nums[0];
        for (int& b : nums) {
            if (b - a > k) {
                a = b;
                ++ans;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func partitionArray(nums []int, k int) int {
	sort.Ints(nums)
	ans, a := 1, nums[0]
	for _, b := range nums {
		if b-a > k {
			a = b
			ans++
		}
	}
	return ans
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function partitionArray(nums: number[], k: number): number {
    nums.sort((a, b) => a - b);
    let ans = 1;
    let a = nums[0];
    for (const b of nums) {
        if (b - a > k) {
            a = b;
            ++ans;
        }
    }
    return ans;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
