---
title: Subarrays with K Different Integers
summary: Subarrays with K Different Integers - Solution Explained
url: "/posts/subarrays-with-k-different-integers"
date: 2020-10-14T16:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Subarrays with K Different Integers LeetCode Solution Explained in all languages", "992", "leetcode question 992", "Subarrays with K Different Integers", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/subarrays-with-k-different-integers.webp
    alt: Subarrays with K Different Integers - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [992. Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers)


## Description

<p>Given an integer array <code>nums</code> and an integer <code>k</code>, return <em>the number of <strong>good subarrays</strong> of </em><code>nums</code>.</p>

<p>A <strong>good array</strong> is an array where the number of different integers in that array is exactly <code>k</code>.</p>

<ul>
	<li>For example, <code>[1,2,3,1,2]</code> has <code>3</code> different integers: <code>1</code>, <code>2</code>, and <code>3</code>.</li>
</ul>

<p>A <strong>subarray</strong> is a <strong>contiguous</strong> part of an array.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,1,2,3], k = 2
<strong>Output:</strong> 7
<strong>Explanation:</strong> Subarrays formed with exactly 2 different integers: [1,2], [2,1], [1,2], [2,3], [1,2,1], [2,1,2], [1,2,1,2]
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,1,3,4], k = 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> Subarrays formed with exactly 3 different integers: [1,2,1,3], [2,1,3], [1,3,4].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i], k &lt;= nums.length</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def subarraysWithKDistinct(self, nums: List[int], k: int) -> int:
        def f(k):
            pos = [0] * len(nums)
            cnt = Counter()
            j = 0
            for i, x in enumerate(nums):
                cnt[x] += 1
                while len(cnt) > k:
                    cnt[nums[j]] -= 1
                    if cnt[nums[j]] == 0:
                        cnt.pop(nums[j])
                    j += 1
                pos[i] = j
            return pos

        return sum(a - b for a, b in zip(f(k - 1), f(k)))
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int subarraysWithKDistinct(int[] nums, int k) {
        int[] left = f(nums, k);
        int[] right = f(nums, k - 1);
        int ans = 0;
        for (int i = 0; i < nums.length; ++i) {
            ans += right[i] - left[i];
        }
        return ans;
    }

    private int[] f(int[] nums, int k) {
        int n = nums.length;
        int[] cnt = new int[n + 1];
        int[] pos = new int[n];
        int s = 0;
        for (int i = 0, j = 0; i < n; ++i) {
            if (++cnt[nums[i]] == 1) {
                ++s;
            }
            for (; s > k; ++j) {
                if (--cnt[nums[j]] == 0) {
                    --s;
                }
            }
            pos[i] = j;
        }
        return pos;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int subarraysWithKDistinct(vector<int>& nums, int k) {
        vector<int> left = f(nums, k);
        vector<int> right = f(nums, k - 1);
        int ans = 0;
        for (int i = 0; i < nums.size(); ++i) {
            ans += right[i] - left[i];
        }
        return ans;
    }

    vector<int> f(vector<int>& nums, int k) {
        int n = nums.size();
        vector<int> pos(n);
        int cnt[n + 1];
        memset(cnt, 0, sizeof(cnt));
        int s = 0;
        for (int i = 0, j = 0; i < n; ++i) {
            if (++cnt[nums[i]] == 1) {
                ++s;
            }
            for (; s > k; ++j) {
                if (--cnt[nums[j]] == 0) {
                    --s;
                }
            }
            pos[i] = j;
        }
        return pos;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func subarraysWithKDistinct(nums []int, k int) (ans int) {
	f := func(k int) []int {
		n := len(nums)
		pos := make([]int, n)
		cnt := make([]int, n+1)
		s, j := 0, 0
		for i, x := range nums {
			cnt[x]++
			if cnt[x] == 1 {
				s++
			}
			for ; s > k; j++ {
				cnt[nums[j]]--
				if cnt[nums[j]] == 0 {
					s--
				}
			}
			pos[i] = j
		}
		return pos
	}
	left, right := f(k), f(k-1)
	for i := range left {
		ans += right[i] - left[i]
	}
	return
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
