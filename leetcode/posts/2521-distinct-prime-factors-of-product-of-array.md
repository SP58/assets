---
title: 2521 Distinct Prime Factors of Product of Array
summary: 2521 Distinct Prime Factors of Product of Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2521 Distinct Prime Factors of Product of Array LeetCode Solution Explained in all languages", "2521 Distinct Prime Factors of Product of Array", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2521 Distinct Prime Factors of Product of Array - Solution Explained/problem-solving.webp
    alt: 2521 Distinct Prime Factors of Product of Array
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2521. Distinct Prime Factors of Product of Array](https://leetcode.com/problems/distinct-prime-factors-of-product-of-array)


## Description

<p>Given an array of positive integers <code>nums</code>, return <em>the number of <strong>distinct prime factors</strong> in the product of the elements of</em> <code>nums</code>.</p>

<p><strong>Note</strong> that:</p>

<ul>
	<li>A number greater than <code>1</code> is called <strong>prime</strong> if it is divisible by only <code>1</code> and itself.</li>
	<li>An integer <code>val1</code> is a factor of another integer <code>val2</code> if <code>val2 / val1</code> is an integer.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,4,3,7,10,6]
<strong>Output:</strong> 4
<strong>Explanation:</strong>
The product of all the elements in nums is: 2 * 4 * 3 * 7 * 10 * 6 = 10080 = 2<sup>5</sup> * 3<sup>2</sup> * 5 * 7.
There are 4 distinct prime factors so we return 4.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,4,8,16]
<strong>Output:</strong> 1
<strong>Explanation:</strong>
The product of all the elements in nums is: 2 * 4 * 8 * 16 = 1024 = 2<sup>10</sup>.
There is 1 distinct prime factor so we return 1.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>2 &lt;= nums[i] &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def distinctPrimeFactors(self, nums: List[int]) -> int:
        s = set()
        for n in nums:
            i = 2
            while i <= n // i:
                if n % i == 0:
                    s.add(i)
                    while n % i == 0:
                        n //= i
                i += 1
            if n > 1:
                s.add(n)
        return len(s)
```

```java
class Solution {
    public int distinctPrimeFactors(int[] nums) {
        Set<Integer> s = new HashSet<>();
        for (int n : nums) {
            for (int i = 2; i <= n / i; ++i) {
                if (n % i == 0) {
                    s.add(i);
                    while (n % i == 0) {
                        n /= i;
                    }
                }
            }
            if (n > 1) {
                s.add(n);
            }
        }
        return s.size();
    }
}
```

```cpp
class Solution {
public:
    int distinctPrimeFactors(vector<int>& nums) {
        unordered_set<int> s;
        for (int& n : nums) {
            for (int i = 2; i <= n / i; ++i) {
                if (n % i == 0) {
                    s.insert(i);
                    while (n % i == 0) {
                        n /= i;
                    }
                }
            }
            if (n > 1) {
                s.insert(n);
            }
        }
        return s.size();
    }
};
```

```go
func distinctPrimeFactors(nums []int) int {
	s := map[int]bool{}
	for _, n := range nums {
		for i := 2; i <= n/i; i++ {
			if n%i == 0 {
				s[i] = true
				for n%i == 0 {
					n /= i
				}
			}
		}
		if n > 1 {
			s[n] = true
		}
	}
	return len(s)
}
```

<!-- tabs:end -->

<!-- end -->