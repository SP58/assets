---
title: Shortest Subarray to be Removed to Make Array Sorted
summary: Shortest Subarray to be Removed to Make Array Sorted - Solution Explained
url: "/posts/shortest-subarray-to-be-removed-to-make-array-sorted"
date: 2020-09-20T10:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Shortest Subarray to be Removed to Make Array Sorted LeetCode Solution Explained in all languages", "1574", "leetcode question 1574", "Shortest Subarray to be Removed to Make Array Sorted", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/shortest-subarray-to-be-removed-to-make-array-sorted.webp
    alt: Shortest Subarray to be Removed to Make Array Sorted - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1574. Shortest Subarray to be Removed to Make Array Sorted](https://leetcode.com/problems/shortest-subarray-to-be-removed-to-make-array-sorted)


## Description

<p>Given an integer array <code>arr</code>, remove a subarray (can be empty) from <code>arr</code> such that the remaining elements in <code>arr</code> are <strong>non-decreasing</strong>.</p>

<p>Return <em>the length of the shortest subarray to remove</em>.</p>

<p>A <strong>subarray</strong> is a contiguous subsequence of the array.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,2,3,10,4,2,3,5]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The shortest subarray we can remove is [10,4,2] of length 3. The remaining elements after that will be [1,2,3,3,5] which are sorted.
Another correct solution is to remove the subarray [3,10,4].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [5,4,3,2,1]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Since the array is strictly decreasing, we can only keep a single element. Therefore we need to remove a subarray of length 4, either [5,4,3,2] or [4,3,2,1].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,2,3]
<strong>Output:</strong> 0
<strong>Explanation:</strong> The array is already non-decreasing. We do not need to remove any elements.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= arr[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def findLengthOfShortestSubarray(self, arr: List[int]) -> int:
        n = len(arr)
        i, j = 0, n - 1
        while i + 1 < n and arr[i] <= arr[i + 1]:
            i += 1
        while j - 1 >= 0 and arr[j - 1] <= arr[j]:
            j -= 1
        if i >= j:
            return 0
        ans = min(n - i - 1, j)
        for l in range(i + 1):
            r = bisect_left(arr, arr[l], lo=j)
            ans = min(ans, r - l - 1)
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int findLengthOfShortestSubarray(int[] arr) {
        int n = arr.length;
        int i = 0, j = n - 1;
        while (i + 1 < n && arr[i] <= arr[i + 1]) {
            ++i;
        }
        while (j - 1 >= 0 && arr[j - 1] <= arr[j]) {
            --j;
        }
        if (i >= j) {
            return 0;
        }
        int ans = Math.min(n - i - 1, j);
        for (int l = 0; l <= i; ++l) {
            int r = search(arr, arr[l], j);
            ans = Math.min(ans, r - l - 1);
        }
        return ans;
    }

    private int search(int[] arr, int x, int left) {
        int right = arr.length;
        while (left < right) {
            int mid = (left + right) >> 1;
            if (arr[mid] >= x) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int findLengthOfShortestSubarray(vector<int>& arr) {
        int n = arr.size();
        int i = 0, j = n - 1;
        while (i + 1 < n && arr[i] <= arr[i + 1]) {
            ++i;
        }
        while (j - 1 >= 0 && arr[j - 1] <= arr[j]) {
            --j;
        }
        if (i >= j) {
            return 0;
        }
        int ans = min(n - 1 - i, j);
        for (int l = 0; l <= i; ++l) {
            int r = lower_bound(arr.begin() + j, arr.end(), arr[l]) - arr.begin();
            ans = min(ans, r - l - 1);
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func findLengthOfShortestSubarray(arr []int) int {
	n := len(arr)
	i, j := 0, n-1
	for i+1 < n && arr[i] <= arr[i+1] {
		i++
	}
	for j-1 >= 0 && arr[j-1] <= arr[j] {
		j--
	}
	if i >= j {
		return 0
	}
	ans := min(n-i-1, j)
	for l := 0; l <= i; l++ {
		r := j + sort.SearchInts(arr[j:], arr[l])
		ans = min(ans, r-l-1)
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
    def findLengthOfShortestSubarray(self, arr: List[int]) -> int:
        n = len(arr)
        i, j = 0, n - 1
        while i + 1 < n and arr[i] <= arr[i + 1]:
            i += 1
        while j - 1 >= 0 and arr[j - 1] <= arr[j]:
            j -= 1
        if i >= j:
            return 0
        ans = min(n - i - 1, j)
        r = j
        for l in range(i + 1):
            while r < n and arr[r] < arr[l]:
                r += 1
            ans = min(ans, r - l - 1)
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int findLengthOfShortestSubarray(int[] arr) {
        int n = arr.length;
        int i = 0, j = n - 1;
        while (i + 1 < n && arr[i] <= arr[i + 1]) {
            ++i;
        }
        while (j - 1 >= 0 && arr[j - 1] <= arr[j]) {
            --j;
        }
        if (i >= j) {
            return 0;
        }
        int ans = Math.min(n - i - 1, j);
        for (int l = 0, r = j; l <= i; ++l) {
            while (r < n && arr[r] < arr[l]) {
                ++r;
            }
            ans = Math.min(ans, r - l - 1);
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
    int findLengthOfShortestSubarray(vector<int>& arr) {
        int n = arr.size();
        int i = 0, j = n - 1;
        while (i + 1 < n && arr[i] <= arr[i + 1]) {
            ++i;
        }
        while (j - 1 >= 0 && arr[j - 1] <= arr[j]) {
            --j;
        }
        if (i >= j) {
            return 0;
        }
        int ans = min(n - 1 - i, j);
        for (int l = 0, r = j; l <= i; ++l) {
            while (r < n && arr[r] < arr[l]) {
                ++r;
            }
            ans = min(ans, r - l - 1);
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func findLengthOfShortestSubarray(arr []int) int {
	n := len(arr)
	i, j := 0, n-1
	for i+1 < n && arr[i] <= arr[i+1] {
		i++
	}
	for j-1 >= 0 && arr[j-1] <= arr[j] {
		j--
	}
	if i >= j {
		return 0
	}
	ans := min(n-i-1, j)
	r := j
	for l := 0; l <= i; l++ {
		for r < n && arr[r] < arr[l] {
			r += 1
		}
		ans = min(ans, r-l-1)
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
