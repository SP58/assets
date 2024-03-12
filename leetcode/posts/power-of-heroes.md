---
title: Power of Heroes
summary: Power of Heroes - Solution Explained
url: "/posts/power-of-heroes"
date: 2020-08-05T07:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Power of Heroes LeetCode Solution Explained in all languages", "2681", "leetcode question 2681", "Power of Heroes", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/power-of-heroes.webp
    alt: Power of Heroes - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2681. Power of Heroes](https://leetcode.com/problems/power-of-heroes)


## Description

<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code> representing the strength of some heroes. The<b> power</b> of a group of heroes is defined as follows:</p>

<ul>
	<li>Let <code>i<sub>0</sub></code>, <code>i<sub>1</sub></code>, ... ,<code>i<sub>k</sub></code> be the indices of the heroes in a group. Then, the power of this group is <code>max(nums[i<sub>0</sub>], nums[i<sub>1</sub>], ... ,nums[i<sub>k</sub>])<sup>2</sup> * min(nums[i<sub>0</sub>], nums[i<sub>1</sub>], ... ,nums[i<sub>k</sub>])</code>.</li>
</ul>

<p>Return <em>the sum of the <strong>power</strong> of all <strong>non-empty</strong> groups of heroes possible.</em> Since the sum could be very large, return it <strong>modulo</strong> <code>10<sup>9 </sup>+ 7</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,4]
<strong>Output:</strong> 141
<strong>Explanation:</strong> 
1<sup>st</sup>&nbsp;group: [2] has power = 2<sup>2</sup>&nbsp;* 2 = 8.
2<sup>nd</sup>&nbsp;group: [1] has power = 1<sup>2</sup> * 1 = 1. 
3<sup>rd</sup>&nbsp;group: [4] has power = 4<sup>2</sup> * 4 = 64. 
4<sup>th</sup>&nbsp;group: [2,1] has power = 2<sup>2</sup> * 1 = 4. 
5<sup>th</sup>&nbsp;group: [2,4] has power = 4<sup>2</sup> * 2 = 32. 
6<sup>th</sup>&nbsp;group: [1,4] has power = 4<sup>2</sup> * 1 = 16. 
​​​​​​​7<sup>th</sup>&nbsp;group: [2,1,4] has power = 4<sup>2</sup>​​​​​​​ * 1 = 16. 
The sum of powers of all groups is 8 + 1 + 64 + 4 + 32 + 16 + 16 = 141.

</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,1]
<strong>Output:</strong> 7
<strong>Explanation:</strong> A total of 7 groups are possible, and the power of each group will be 1. Therefore, the sum of the powers of all groups is 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def sumOfPower(self, nums: List[int]) -> int:
        mod = 10**9 + 7
        nums.sort()
        ans = 0
        p = 0
        for x in nums[::-1]:
            ans = (ans + (x * x % mod) * x) % mod
            ans = (ans + x * p) % mod
            p = (p * 2 + x * x) % mod
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int sumOfPower(int[] nums) {
        final int mod = (int) 1e9 + 7;
        Arrays.sort(nums);
        long ans = 0, p = 0;
        for (int i = nums.length - 1; i >= 0; --i) {
            long x = nums[i];
            ans = (ans + (x * x % mod) * x) % mod;
            ans = (ans + x * p % mod) % mod;
            p = (p * 2 + x * x % mod) % mod;
        }
        return (int) ans;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int sumOfPower(vector<int>& nums) {
        const int mod = 1e9 + 7;
        sort(nums.rbegin(), nums.rend());
        long long ans = 0, p = 0;
        for (long long x : nums) {
            ans = (ans + (x * x % mod) * x) % mod;
            ans = (ans + x * p % mod) % mod;
            p = (p * 2 + x * x % mod) % mod;
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func sumOfPower(nums []int) (ans int) {
	const mod = 1e9 + 7
	sort.Ints(nums)
	p := 0
	for i := len(nums) - 1; i >= 0; i-- {
		x := nums[i]
		ans = (ans + (x*x%mod)*x) % mod
		ans = (ans + x*p%mod) % mod
		p = (p*2 + x*x%mod) % mod
	}
	return
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function sumOfPower(nums: number[]): number {
    const mod = 10 ** 9 + 7;
    nums.sort((a, b) => a - b);
    let ans = 0;
    let p = 0;
    for (let i = nums.length - 1; i >= 0; --i) {
        const x = BigInt(nums[i]);
        ans = (ans + Number((x * x * x) % BigInt(mod))) % mod;
        ans = (ans + Number((x * BigInt(p)) % BigInt(mod))) % mod;
        p = Number((BigInt(p) * 2n + x * x) % BigInt(mod));
    }
    return ans;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
