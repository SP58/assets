---
title: Single Element in a Sorted Array
summary: Single Element in a Sorted Array - Solution Explained
url: "/posts/single-element-in-a-sorted-array"
date: 2020-11-02T12:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Single Element in a Sorted Array LeetCode Solution Explained in all languages", "540", "leetcode question 540", "Single Element in a Sorted Array", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/single-element-in-a-sorted-array.webp
    alt: Single Element in a Sorted Array - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array)


## Description

<p>You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.</p>

<p>Return <em>the single element that appears only once</em>.</p>

<p>Your solution must run in <code>O(log n)</code> time and <code>O(1)</code> space.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,1,2,3,3,4,4,8,8]
<strong>Output:</strong> 2
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [3,3,7,7,10,11,11]
<strong>Output:</strong> 10
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def singleNonDuplicate(self, nums: List[int]) -> int:
        left, right = 0, len(nums) - 1
        while left < right:
            mid = (left + right) >> 1
            # Equals to: if (mid % 2 == 0 and nums[mid] != nums[mid + 1]) or (mid % 2 == 1 and nums[mid] != nums[mid - 1]):
            if nums[mid] != nums[mid ^ 1]:
                right = mid
            else:
                left = mid + 1
        return nums[left]
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = (left + right) >> 1;
            // if ((mid % 2 == 0 && nums[mid] != nums[mid + 1]) || (mid % 2 == 1 && nums[mid] !=
            // nums[mid - 1])) {
            if (nums[mid] != nums[mid ^ 1]) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return nums[left];
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        while (left < right) {
            int mid = left + right >> 1;
            if (nums[mid] != nums[mid ^ 1])
                right = mid;
            else
                left = mid + 1;
        }
        return nums[left];
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func singleNonDuplicate(nums []int) int {
	left, right := 0, len(nums)-1
	for left < right {
		mid := (left + right) >> 1
		if nums[mid] != nums[mid^1] {
			right = mid
		} else {
			left = mid + 1
		}
	}
	return nums[left]
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function singleNonDuplicate(nums: number[]): number {
    let left = 0,
        right = nums.length - 1;
    while (left < right) {
        const mid = (left + right) >> 1;
        if (nums[mid] != nums[mid ^ 1]) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return nums[left];
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn single_non_duplicate(nums: Vec<i32>) -> i32 {
        let mut l = 0;
        let mut r = nums.len() - 1;
        while l < r {
            let mid = (l + r) >> 1;
            if nums[mid] == nums[mid ^ 1] {
                l = mid + 1;
            } else {
                r = mid;
            }
        }
        nums[l]
    }
}
```
{{< /terminal >}}

{{< terminal title="C Code" >}}
```c
int singleNonDuplicate(int* nums, int numsSize) {
    int left = 0;
    int right = numsSize - 1;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] == nums[mid ^ 1]) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    return nums[left];
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
