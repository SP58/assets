---
title: Longest Square Streak in an Array
summary: Longest Square Streak in an Array - Solution Explained
url: "/posts/longest-square-streak-in-an-array"
date: 2020-08-12T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Longest Square Streak in an Array LeetCode Solution Explained in all languages", "2501", "leetcode question 2501", "Longest Square Streak in an Array", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/longest-square-streak-in-an-array.webp
    alt: Longest Square Streak in an Array - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2501. Longest Square Streak in an Array](https://leetcode.com/problems/longest-square-streak-in-an-array)


## Description

<p>You are given an integer array <code>nums</code>. A subsequence of <code>nums</code> is called a <strong>square streak</strong> if:</p>

<ul>
	<li>The length of the subsequence is at least <code>2</code>, and</li>
	<li><strong>after</strong> sorting the subsequence, each element (except the first element) is the <strong>square</strong> of the previous number.</li>
</ul>

<p>Return<em> the length of the <strong>longest square streak</strong> in </em><code>nums</code><em>, or return </em><code>-1</code><em> if there is no <strong>square streak</strong>.</em></p>

<p>A <strong>subsequence</strong> is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,3,6,16,8,2]
<strong>Output:</strong> 3
<strong>Explanation:</strong> Choose the subsequence [4,16,2]. After sorting it, it becomes [2,4,16].
- 4 = 2 * 2.
- 16 = 4 * 4.
Therefore, [4,16,2] is a square streak.
It can be shown that every subsequence of length 4 is not a square streak.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,3,5,6,7]
<strong>Output:</strong> -1
<strong>Explanation:</strong> There is no square streak in nums so return -1.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>2 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def longestSquareStreak(self, nums: List[int]) -> int:
        s = set(nums)
        ans = -1
        for v in nums:
            t = 0
            while v in s:
                v *= v
                t += 1
            if t > 1:
                ans = max(ans, t)
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int longestSquareStreak(int[] nums) {
        Set<Integer> s = new HashSet<>();
        for (int v : nums) {
            s.add(v);
        }
        int ans = -1;
        for (int v : nums) {
            int t = 0;
            while (s.contains(v)) {
                v *= v;
                ++t;
            }
            if (t > 1) {
                ans = Math.max(ans, t);
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
    int longestSquareStreak(vector<int>& nums) {
        unordered_set<long long> s(nums.begin(), nums.end());
        int ans = -1;
        for (int& v : nums) {
            int t = 0;
            long long x = v;
            while (s.count(x)) {
                x *= x;
                ++t;
            }
            if (t > 1) ans = max(ans, t);
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func longestSquareStreak(nums []int) int {
	s := map[int]bool{}
	for _, v := range nums {
		s[v] = true
	}
	ans := -1
	for _, v := range nums {
		t := 0
		for s[v] {
			v *= v
			t++
		}
		if t > 1 && t > ans {
			ans = t
		}
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def longestSquareStreak(self, nums: List[int]) -> int:
        @cache
        def dfs(x):
            if x not in s:
                return 0
            return 1 + dfs(x * x)

        s = set(nums)
        ans = max(dfs(x) for x in nums)
        return -1 if ans < 2 else ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    private Map<Integer, Integer> f = new HashMap<>();
    private Set<Integer> s = new HashSet<>();

    public int longestSquareStreak(int[] nums) {
        for (int v : nums) {
            s.add(v);
        }
        int ans = 0;
        for (int v : nums) {
            ans = Math.max(ans, dfs(v));
        }
        return ans < 2 ? -1 : ans;
    }

    private int dfs(int x) {
        if (!s.contains(x)) {
            return 0;
        }
        if (f.containsKey(x)) {
            return f.get(x);
        }
        int ans = 1 + dfs(x * x);
        f.put(x, ans);
        return ans;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int longestSquareStreak(vector<int>& nums) {
        unordered_set<long long> s(nums.begin(), nums.end());
        int ans = 0;
        unordered_map<int, int> f;
        function<int(int)> dfs = [&](int x) -> int {
            if (!s.count(x)) return 0;
            if (f.count(x)) return f[x];
            long long t = 1ll * x * x;
            if (t > INT_MAX) return 1;
            f[x] = 1 + dfs(x * x);
            return f[x];
        };
        for (int& v : nums) ans = max(ans, dfs(v));
        return ans < 2 ? -1 : ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func longestSquareStreak(nums []int) (ans int) {
	s := map[int]bool{}
	for _, v := range nums {
		s[v] = true
	}
	f := map[int]int{}
	var dfs func(int) int
	dfs = func(x int) int {
		if !s[x] {
			return 0
		}
		if v, ok := f[x]; ok {
			return v
		}
		f[x] = 1 + dfs(x*x)
		return f[x]
	}
	for _, v := range nums {
		if t := dfs(v); ans < t {
			ans = t
		}
	}
	if ans < 2 {
		return -1
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
