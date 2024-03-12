---
title: Partition Array Into Three Parts With Equal Sum
summary: Partition Array Into Three Parts With Equal Sum - Solution Explained
url: "/posts/partition-array-into-three-parts-with-equal-sum"
date: 2020-10-13T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Partition Array Into Three Parts With Equal Sum LeetCode Solution Explained in all languages", "1013", "leetcode question 1013", "Partition Array Into Three Parts With Equal Sum", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/partition-array-into-three-parts-with-equal-sum.webp
    alt: Partition Array Into Three Parts With Equal Sum - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1013. Partition Array Into Three Parts With Equal Sum](https://leetcode.com/problems/partition-array-into-three-parts-with-equal-sum)


## Description

<p>Given an array of integers <code>arr</code>, return <code>true</code> if we can partition the array into three <strong>non-empty</strong> parts with equal sums.</p>

<p>Formally, we can partition the array if we can find indexes <code>i + 1 &lt; j</code> with <code>(arr[0] + arr[1] + ... + arr[i] == arr[i + 1] + arr[i + 2] + ... + arr[j - 1] == arr[j] + arr[j + 1] + ... + arr[arr.length - 1])</code></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [0,2,1,-6,6,-7,9,1,2,0,1]
<strong>Output:</strong> true
<strong>Explanation: </strong>0 + 2 + 1 = -6 + 6 - 7 + 9 + 1 = 2 + 0 + 1
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [0,2,1,-6,6,7,9,-1,2,0,1]
<strong>Output:</strong> false
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [3,3,6,5,-2,2,5,1,-9,4]
<strong>Output:</strong> true
<strong>Explanation: </strong>3 + 3 = 6 = 5 - 2 + 2 + 5 + 1 - 9 + 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= arr.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= arr[i] &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def canThreePartsEqualSum(self, arr: List[int]) -> bool:
        s = sum(arr)
        if s % 3 != 0:
            return False
        i, j = 0, len(arr) - 1
        a = b = 0
        while i < len(arr):
            a += arr[i]
            if a == s // 3:
                break
            i += 1
        while ~j:
            b += arr[j]
            if b == s // 3:
                break
            j -= 1
        return i < j - 1
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean canThreePartsEqualSum(int[] arr) {
        int s = 0;
        for (int v : arr) {
            s += v;
        }
        if (s % 3 != 0) {
            return false;
        }
        int i = 0, j = arr.length - 1;
        int a = 0, b = 0;
        while (i < arr.length) {
            a += arr[i];
            if (a == s / 3) {
                break;
            }
            ++i;
        }
        while (j >= 0) {
            b += arr[j];
            if (b == s / 3) {
                break;
            }
            --j;
        }
        return i < j - 1;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool canThreePartsEqualSum(vector<int>& arr) {
        int s = 0;
        for (int v : arr) s += v;
        if (s % 3) return false;
        int i = 0, j = arr.size() - 1;
        int a = 0, b = 0;
        while (i < arr.size()) {
            a += arr[i];
            if (a == s / 3) {
                break;
            }
            ++i;
        }
        while (~j) {
            b += arr[j];
            if (b == s / 3) {
                break;
            }
            --j;
        }
        return i < j - 1;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func canThreePartsEqualSum(arr []int) bool {
	s := 0
	for _, v := range arr {
		s += v
	}
	if s%3 != 0 {
		return false
	}
	i, j := 0, len(arr)-1
	a, b := 0, 0
	for i < len(arr) {
		a += arr[i]
		if a == s/3 {
			break
		}
		i++
	}
	for j >= 0 {
		b += arr[j]
		if b == s/3 {
			break
		}
		j--
	}
	return i < j-1
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
