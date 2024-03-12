---
title: Bitwise ORs of Subarrays
summary: Bitwise ORs of Subarrays - Solution Explained
url: "/posts/bitwise-ors-of-subarrays"
date: 2020-10-18T14:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Bitwise ORs of Subarrays LeetCode Solution Explained in all languages", "898", "leetcode question 898", "Bitwise ORs of Subarrays", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/bitwise-ors-of-subarrays.webp
    alt: Bitwise ORs of Subarrays - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [898. Bitwise ORs of Subarrays](https://leetcode.com/problems/bitwise-ors-of-subarrays)


## Description

<p>Given an integer array <code>arr</code>, return <em>the number of distinct bitwise ORs of all the non-empty subarrays of</em> <code>arr</code>.</p>

<p>The bitwise OR of a subarray is the bitwise OR of each integer in the subarray. The bitwise OR of a subarray of one integer is that integer.</p>

<p>A <strong>subarray</strong> is a contiguous non-empty sequence of elements within an array.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [0]
<strong>Output:</strong> 1
<strong>Explanation:</strong> There is only one possible result: 0.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,1,2]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The possible subarrays are [1], [1], [2], [1, 1], [1, 2], [1, 1, 2].
These yield the results 1, 1, 2, 1, 3, 3.
There are 3 unique values, so the answer is 3.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,2,4]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The possible results are 1, 2, 3, 4, 6, and 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= arr[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1: Hash Table

The problem asks for the number of unique bitwise OR operations results of subarrays. If we enumerate the end position $i$ of the subarray, the number of bitwise OR operations results of the subarray ending at $i-1$ does not exceed $32$. This is because the bitwise OR operation is a monotonically increasing operation.

Therefore, we use a hash table $ans$ to record all the results of the bitwise OR operations of subarrays, and a hash table $s$ to record the results of the bitwise OR operations of subarrays ending with the current element. Initially, $s$ only contains one element $0$.

Next, we enumerate the end position $i$ of the subarray. The result of the bitwise OR operation of the subarray ending at $i$ is the set of results of the bitwise OR operation of the subarray ending at $i-1$ and $a[i]$, plus $a[i]$ itself. We use a hash table $t$ to record the results of the bitwise OR operation of the subarray ending at $i$, then we update $s = t$, and add all elements in $t$ to $ans$.

Finally, we return the number of elements in the hash table $ans$.

The time complexity is $O(n \times \log M)$, and the space complexity is $O(n \times \log M)$. Here, $n$ and $M$ are the length of the array and the maximum value in the array, respectively.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def subarrayBitwiseORs(self, arr: List[int]) -> int:
        s = {0}
        ans = set()
        for x in arr:
            s = {x | y for y in s} | {x}
            ans |= s
        return len(ans)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int subarrayBitwiseORs(int[] arr) {
        Set<Integer> s = new HashSet<>();
        s.add(0);
        Set<Integer> ans = new HashSet<>();
        for (int x : arr) {
            Set<Integer> t = new HashSet<>();
            for (int y : s) {
                t.add(x | y);
            }
            t.add(x);
            s = t;
            ans.addAll(s);
        }
        return ans.size();
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int subarrayBitwiseORs(vector<int>& arr) {
        unordered_set<int> s{{0}};
        unordered_set<int> ans;
        for (int& x : arr) {
            unordered_set<int> t{{x}};
            for (int y : s) {
                t.insert(x | y);
            }
            s = move(t);
            ans.insert(s.begin(), s.end());
        }
        return ans.size();
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func subarrayBitwiseORs(arr []int) int {
	ans := map[int]bool{}
	s := map[int]bool{0: true}
	for _, x := range arr {
		t := map[int]bool{x: true}
		for y := range s {
			t[x|y] = true
		}
		s = t
		for y := range s {
			ans[y] = true
		}
	}
	return len(ans)
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function subarrayBitwiseORs(arr: number[]): number {
    const s: Set<number> = new Set();
    const ans: Set<number> = new Set();
    for (const x of arr) {
        const t: Set<number> = new Set();
        for (const y of s) {
            t.add(x | y);
        }
        t.add(x);
        s.clear();
        for (const y of t) {
            s.add(y);
            ans.add(y);
        }
    }
    return ans.size;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
