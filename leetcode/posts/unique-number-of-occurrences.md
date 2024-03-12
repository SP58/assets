---
title: Unique Number of Occurrences
summary: Unique Number of Occurrences - Solution Explained
url: "/posts/unique-number-of-occurrences"
date: 2020-10-05T17:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Unique Number of Occurrences LeetCode Solution Explained in all languages", "1207", "leetcode question 1207", "Unique Number of Occurrences", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/unique-number-of-occurrences.webp
    alt: Unique Number of Occurrences - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1207. Unique Number of Occurrences](https://leetcode.com/problems/unique-number-of-occurrences)


## Description

<p>Given an array of integers <code>arr</code>, return <code>true</code> <em>if the number of occurrences of each value in the array is <strong>unique</strong> or </em><code>false</code><em> otherwise</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,2,2,1,1,3]
<strong>Output:</strong> true
<strong>Explanation:</strong>&nbsp;The value 1 has 3 occurrences, 2 has 2 and 3 has 1. No two values have the same number of occurrences.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,2]
<strong>Output:</strong> false
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [-3,0,1,-3,1,1,1,-3,10,0]
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 1000</code></li>
	<li><code>-1000 &lt;= arr[i] &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1: Hash Table

We use a hash table $cnt$ to count the frequency of each number in the array $arr$, and then use another hash table $vis$ to count the types of frequencies. Finally, we check whether the sizes of $cnt$ and $vis$ are equal.

The time complexity is $O(n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the array $arr$.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def uniqueOccurrences(self, arr: List[int]) -> bool:
        cnt = Counter(arr)
        return len(set(cnt.values())) == len(cnt)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        Map<Integer, Integer> cnt = new HashMap<>();
        for (int x : arr) {
            cnt.merge(x, 1, Integer::sum);
        }
        return new HashSet<>(cnt.values()).size() == cnt.size();
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool uniqueOccurrences(vector<int>& arr) {
        unordered_map<int, int> cnt;
        for (int& x : arr) {
            ++cnt[x];
        }
        unordered_set<int> vis;
        for (auto& [_, v] : cnt) {
            if (vis.count(v)) {
                return false;
            }
            vis.insert(v);
        }
        return true;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func uniqueOccurrences(arr []int) bool {
	cnt := map[int]int{}
	for _, x := range arr {
		cnt[x]++
	}
	vis := map[int]bool{}
	for _, v := range cnt {
		if vis[v] {
			return false
		}
		vis[v] = true
	}
	return true
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function uniqueOccurrences(arr: number[]): boolean {
    const cnt: Map<number, number> = new Map();
    for (const x of arr) {
        cnt.set(x, (cnt.get(x) || 0) + 1);
    }
    return cnt.size === new Set(cnt.values()).size;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
