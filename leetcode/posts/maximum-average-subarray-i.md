---
title: Maximum Average Subarray I
summary: Maximum Average Subarray I - Solution Explained
url: "/posts/maximum-average-subarray-i"
date: 2020-10-29T05:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Maximum Average Subarray I LeetCode Solution Explained in all languages", "643", "leetcode question 643", "Maximum Average Subarray I", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/maximum-average-subarray-i.webp
    alt: Maximum Average Subarray I - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i)


## Description

<p>You are given an integer array <code>nums</code> consisting of <code>n</code> elements, and an integer <code>k</code>.</p>

<p>Find a contiguous subarray whose <strong>length is equal to</strong> <code>k</code> that has the maximum average value and return <em>this value</em>. Any answer with a calculation error less than <code>10<sup>-5</sup></code> will be accepted.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,12,-5,-6,50,3], k = 4
<strong>Output:</strong> 12.75000
<strong>Explanation:</strong> Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [5], k = 1
<strong>Output:</strong> 5.00000
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= k &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def findMaxAverage(self, nums: List[int], k: int) -> float:
        s = sum(nums[:k])
        ans = s
        for i in range(k, len(nums)):
            s += nums[i] - nums[i - k]
            ans = max(ans, s)
        return ans / k
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        int s = 0;
        for (int i = 0; i < k; ++i) {
            s += nums[i];
        }
        int ans = s;
        for (int i = k; i < nums.length; ++i) {
            s += (nums[i] - nums[i - k]);
            ans = Math.max(ans, s);
        }
        return ans * 1.0 / k;
    }
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function findMaxAverage(nums: number[], k: number): number {
    let n = nums.length;
    let ans = 0;
    let sum = 0;
    // 前k
    for (let i = 0; i < k; i++) {
        sum += nums[i];
    }
    ans = sum;
    for (let i = k; i < n; i++) {
        sum += nums[i] - nums[i - k];
        ans = Math.max(ans, sum);
    }
    return ans / k;
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn find_max_average(nums: Vec<i32>, k: i32) -> f64 {
        let k = k as usize;
        let n = nums.len();
        let mut sum = nums.iter().take(k).sum::<i32>();
        let mut max = sum;
        for i in k..n {
            sum += nums[i] - nums[i - k];
            max = max.max(sum);
        }
        f64::from(max) / f64::from(k as i32)
    }
}
```
{{< /terminal >}}

{{< terminal title="PHP Code" >}}
```php
class Solution {
    /**
     * @param Integer[] $nums
     * @param Integer $k
     * @return Float
     */
    function findMaxAverage($nums, $k) {
        $sum = 0;
        for ($i = 0; $i < $k; $i++) {
            $sum += $nums[$i];
        }
        $max = $sum;
        for ($j = $k; $j < count($nums); $j++) {
            $sum = $sum - $nums[$j - $k] + $nums[$j];
            $max = max($max, $sum);
        }
        return $max / $k;
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
