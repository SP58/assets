---
title: Neither Minimum nor Maximum
summary: Neither Minimum nor Maximum - Solution Explained
url: "/posts/neither-minimum-nor-maximum"
date: 2020-08-03T03:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Neither Minimum nor Maximum LeetCode Solution Explained in all languages", "2733", "leetcode question 2733", "Neither Minimum nor Maximum", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/neither-minimum-nor-maximum.webp
    alt: Neither Minimum nor Maximum - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2733. Neither Minimum nor Maximum](https://leetcode.com/problems/neither-minimum-nor-maximum)


## Description

<p>Given an integer array <code>nums</code> containing <strong>distinct</strong> <strong>positive</strong> integers, find and return <strong>any</strong> number from the array that is neither the <strong>minimum</strong> nor the <strong>maximum</strong> value in the array, or <strong><code>-1</code></strong> if there is no such number.</p>

<p>Return <em>the selected integer.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,2,1,4]
<strong>Output:</strong> 2
<strong>Explanation:</strong> In this example, the minimum value is 1 and the maximum value is 4. Therefore, either 2 or 3 can be valid answers.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2]
<strong>Output:</strong> -1
<strong>Explanation:</strong> Since there is no number in nums that is neither the maximum nor the minimum, we cannot select a number that satisfies the given condition. Therefore, there is no answer.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,3]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Since 2 is neither the maximum nor the minimum value in nums, it is the only valid answer. 
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 100</code></li>
	<li>All values in <code>nums</code> are distinct</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def findNonMinOrMax(self, nums: List[int]) -> int:
        return -1 if len(nums) < 3 else sorted(nums)[1]
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int findNonMinOrMax(int[] nums) {
        int mi = 100, mx = 0;
        for (int x : nums) {
            mi = Math.min(mi, x);
            mx = Math.max(mx, x);
        }
        for (int x : nums) {
            if (x != mi && x != mx) {
                return x;
            }
        }
        return -1;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int findNonMinOrMax(vector<int>& nums) {
        int mi = *min_element(nums.begin(), nums.end());
        int mx = *max_element(nums.begin(), nums.end());
        for (int x : nums) {
            if (x != mi && x != mx) {
                return x;
            }
        }
        return -1;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func findNonMinOrMax(nums []int) int {
	mi, mx := slices.Min(nums), slices.Max(nums)
	for _, x := range nums {
		if x != mi && x != mx {
			return x
		}
	}
	return -1
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn find_non_min_or_max(nums: Vec<i32>) -> i32 {
        let mut mi = 100;
        let mut mx = 0;

        for &ele in nums.iter() {
            if ele < mi {
                mi = ele;
            }
            if ele > mx {
                mx = ele;
            }
        }

        for &ele in nums.iter() {
            if ele != mi && ele != mx {
                return ele;
            }
        }

        -1
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def findNonMinOrMax(self, nums: List[int]) -> int:
        mi, mx = min(nums), max(nums)
        for x in nums:
            if x != mi and x != mx:
                return x
        return -1
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
