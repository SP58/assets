---
title: Minimum Elements to Add to Form a Given Sum
summary: Minimum Elements to Add to Form a Given Sum - Solution Explained
url: "/posts/minimum-elements-to-add-to-form-a-given-sum"
date: 2020-09-11T15:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Minimum Elements to Add to Form a Given Sum LeetCode Solution Explained in all languages", "1785", "leetcode question 1785", "Minimum Elements to Add to Form a Given Sum", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/minimum-elements-to-add-to-form-a-given-sum.webp
    alt: Minimum Elements to Add to Form a Given Sum - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1785. Minimum Elements to Add to Form a Given Sum](https://leetcode.com/problems/minimum-elements-to-add-to-form-a-given-sum)


## Description

<p>You are given an integer array <code>nums</code> and two integers <code>limit</code> and <code>goal</code>. The array <code>nums</code> has an interesting property that <code>abs(nums[i]) &lt;= limit</code>.</p>

<p>Return <em>the minimum number of elements you need to add to make the sum of the array equal to </em><code>goal</code>. The array must maintain its property that <code>abs(nums[i]) &lt;= limit</code>.</p>

<p>Note that <code>abs(x)</code> equals <code>x</code> if <code>x &gt;= 0</code>, and <code>-x</code> otherwise.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,-1,1], limit = 3, goal = -4
<strong>Output:</strong> 2
<strong>Explanation:</strong> You can add -2 and -3, then the sum of the array will be 1 - 1 + 1 - 2 - 3 = -4.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,-10,9,1], limit = 100, goal = 0
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= limit &lt;= 10<sup>6</sup></code></li>
	<li><code>-limit &lt;= nums[i] &lt;= limit</code></li>
	<li><code>-10<sup>9</sup> &lt;= goal &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1: Greedy

First, we calculate the sum of the array elements $s$, and then calculate the difference $d$ between $s$ and $goal$.

The number of elements to be added is the absolute value of $d$ divided by $limit$ and rounded up, that is, $\lceil \frac{|d|}{limit} \rceil$.

Note that in this problem, the data range of array elements is $[-10^6, 10^6]$, the maximum number of elements is $10^5$, the total sum $s$ and the difference $d$ may exceed the range of 32-bit integers, so we need to use 64-bit integers.

The time complexity is $O(n)$, and the space complexity is $O(1)$. Here, $n$ is the length of the array $nums$.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def minElements(self, nums: List[int], limit: int, goal: int) -> int:
        d = abs(sum(nums) - goal)
        return (d + limit - 1) // limit
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int minElements(int[] nums, int limit, int goal) {
        // long s = Arrays.stream(nums).asLongStream().sum();
        long s = 0;
        for (int v : nums) {
            s += v;
        }
        long d = Math.abs(s - goal);
        return (int) ((d + limit - 1) / limit);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int minElements(vector<int>& nums, int limit, int goal) {
        long long s = accumulate(nums.begin(), nums.end(), 0ll);
        long long d = abs(s - goal);
        return (d + limit - 1) / limit;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func minElements(nums []int, limit int, goal int) int {
	s := 0
	for _, v := range nums {
		s += v
	}
	d := abs(s - goal)
	return (d + limit - 1) / limit
}

func abs(x int) int {
	if x < 0 {
		return -x
	}
	return x
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function minElements(nums: number[], limit: number, goal: number): number {
    const sum = nums.reduce((r, v) => r + v, 0);
    const diff = Math.abs(goal - sum);
    return Math.floor((diff + limit - 1) / limit);
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn min_elements(nums: Vec<i32>, limit: i32, goal: i32) -> i32 {
        let limit = limit as i64;
        let goal = goal as i64;
        let mut sum = 0;
        for &num in nums.iter() {
            sum += num as i64;
        }
        let diff = (goal - sum).abs();
        ((diff + limit - 1) / limit) as i32
    }
}
```
{{< /terminal >}}

{{< terminal title="C Code" >}}
```c
int minElements(int* nums, int numsSize, int limit, int goal) {
    long long sum = 0;
    for (int i = 0; i < numsSize; i++) {
        sum += nums[i];
    }
    long long diff = labs(goal - sum);
    return (diff + limit - 1) / limit;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
