---
title: Maximum Average Subarray II
summary: Maximum Average Subarray II - Solution Explained
url: "/posts/maximum-average-subarray-ii"
date: 2020-10-29T04:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Maximum Average Subarray II LeetCode Solution Explained in all languages", "644", "leetcode question 644", "Maximum Average Subarray II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/maximum-average-subarray-ii.webp
    alt: Maximum Average Subarray II - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [644. Maximum Average Subarray II](https://leetcode.com/problems/maximum-average-subarray-ii)


## Description

<p>You are given an integer array <code>nums</code> consisting of <code>n</code> elements, and an integer <code>k</code>.</p>

<p>Find a contiguous subarray whose <strong>length is greater than or equal to</strong> <code>k</code> that has the maximum average value and return <em>this value</em>. Any answer with a calculation error less than <code>10<sup>-5</sup></code> will be accepted.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,12,-5,-6,50,3], k = 4
<strong>Output:</strong> 12.75000
<b>Explanation:
</b>- When the length is 4, averages are [0.5, 12.75, 10.5] and the maximum average is 12.75
- When the length is 5, averages are [10.4, 10.8] and the maximum average is 10.8
- When the length is 6, averages are [9.16667] and the maximum average is 9.16667
The maximum average is when we choose a subarray of length 4 (i.e., the sub array [12, -5, -6, 50]) which has the max average 12.75, so we return 12.75
Note that we do not consider the subarrays of length &lt; 4.
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
	<li><code>1 &lt;= k &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def findMaxAverage(self, nums: List[int], k: int) -> float:
        def check(v: float) -> bool:
            s = sum(nums[:k]) - k * v
            if s >= 0:
                return True
            t = mi = 0
            for i in range(k, len(nums)):
                s += nums[i] - v
                t += nums[i - k] - v
                mi = min(mi, t)
                if s >= mi:
                    return True
            return False

        eps = 1e-5
        l, r = min(nums), max(nums)
        while r - l >= eps:
            mid = (l + r) / 2
            if check(mid):
                l = mid
            else:
                r = mid
        return l
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        double eps = 1e-5;
        double l = 1e10, r = -1e10;
        for (int x : nums) {
            l = Math.min(l, x);
            r = Math.max(r, x);
        }
        while (r - l >= eps) {
            double mid = (l + r) / 2;
            if (check(nums, k, mid)) {
                l = mid;
            } else {
                r = mid;
            }
        }
        return l;
    }

    private boolean check(int[] nums, int k, double v) {
        double s = 0;
        for (int i = 0; i < k; ++i) {
            s += nums[i] - v;
        }
        if (s >= 0) {
            return true;
        }
        double t = 0;
        double mi = 0;
        for (int i = k; i < nums.length; ++i) {
            s += nums[i] - v;
            t += nums[i - k] - v;
            mi = Math.min(mi, t);
            if (s >= mi) {
                return true;
            }
        }
        return false;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        double eps = 1e-5;
        double l = *min_element(nums.begin(), nums.end());
        double r = *max_element(nums.begin(), nums.end());
        auto check = [&](double v) {
            double s = 0;
            for (int i = 0; i < k; ++i) {
                s += nums[i] - v;
            }
            if (s >= 0) {
                return true;
            }
            double t = 0;
            double mi = 0;
            for (int i = k; i < nums.size(); ++i) {
                s += nums[i] - v;
                t += nums[i - k] - v;
                mi = min(mi, t);
                if (s >= mi) {
                    return true;
                }
            }
            return false;
        };
        while (r - l >= eps) {
            double mid = (l + r) / 2;
            if (check(mid)) {
                l = mid;
            } else {
                r = mid;
            }
        }
        return l;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func findMaxAverage(nums []int, k int) float64 {
	eps := 1e-5
	l := float64(slices.Min(nums))
	r := float64(slices.Max(nums))
	check := func(v float64) bool {
		s := 0.0
		for _, x := range nums[:k] {
			s += float64(x) - v
		}
		if s >= 0 {
			return true
		}
		t := 0.0
		mi := 0.0
		for i := k; i < len(nums); i++ {
			s += float64(nums[i]) - v
			t += float64(nums[i-k]) - v
			mi = math.Min(mi, t)
			if s >= mi {
				return true
			}
		}
		return false
	}
	for r-l >= eps {
		mid := (l + r) / 2
		if check(mid) {
			l = mid
		} else {
			r = mid
		}
	}
	return l
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function findMaxAverage(nums: number[], k: number): number {
    const eps = 1e-5;
    let l = Math.min(...nums);
    let r = Math.max(...nums);
    const check = (v: number): boolean => {
        let s = nums.slice(0, k).reduce((a, b) => a + b) - v * k;
        if (s >= 0) {
            return true;
        }
        let t = 0;
        let mi = 0;
        for (let i = k; i < nums.length; ++i) {
            s += nums[i] - v;
            t += nums[i - k] - v;
            mi = Math.min(mi, t);
            if (s >= mi) {
                return true;
            }
        }
        return false;
    };
    while (r - l >= eps) {
        const mid = (l + r) / 2;
        if (check(mid)) {
            l = mid;
        } else {
            r = mid;
        }
    }
    return l;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
