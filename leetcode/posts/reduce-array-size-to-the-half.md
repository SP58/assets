---
title: Reduce Array Size to The Half
summary: Reduce Array Size to The Half - Solution Explained
url: "/posts/reduce-array-size-to-the-half"
date: 2020-09-30T06:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Reduce Array Size to The Half LeetCode Solution Explained in all languages", "1338", "leetcode question 1338", "Reduce Array Size to The Half", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/reduce-array-size-to-the-half.webp
    alt: Reduce Array Size to The Half - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1338. Reduce Array Size to The Half](https://leetcode.com/problems/reduce-array-size-to-the-half)


## Description

<p>You are given an integer array <code>arr</code>. You can choose a set of integers and remove all the occurrences of these integers in the array.</p>

<p>Return <em>the minimum size of the set so that <strong>at least</strong> half of the integers of the array are removed</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [3,3,3,3,5,5,5,2,2,7]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Choosing {3,7} will make the new array [5,5,5,2,2] which has size 5 (i.e equal to half of the size of the old array).
Possible sets of size 2 are {3,5},{3,2},{5,2}.
Choosing set {2,7} is not possible as it will make the new array [3,3,3,3,5,5,5] which has a size greater than half of the size of the old array.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [7,7,7,7,7,7]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The only possible set you can choose is {7}. This will make the new array empty.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= arr.length &lt;= 10<sup>5</sup></code></li>
	<li><code>arr.length</code> is even.</li>
	<li><code>1 &lt;= arr[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def minSetSize(self, arr: List[int]) -> int:
        cnt = Counter(arr)
        ans = m = 0
        for _, v in cnt.most_common():
            m += v
            ans += 1
            if m * 2 >= len(arr):
                break
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int minSetSize(int[] arr) {
        int mx = 0;
        for (int x : arr) {
            mx = Math.max(mx, x);
        }
        int[] cnt = new int[mx + 1];
        for (int x : arr) {
            ++cnt[x];
        }
        Arrays.sort(cnt);
        int ans = 0;
        int m = 0;
        for (int i = mx;; --i) {
            if (cnt[i] > 0) {
                m += cnt[i];
                ++ans;
                if (m * 2 >= arr.length) {
                    return ans;
                }
            }
        }
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    int minSetSize(vector<int>& arr) {
        int mx = *max_element(arr.begin(), arr.end());
        int cnt[mx + 1];
        memset(cnt, 0, sizeof(cnt));
        for (int& x : arr) {
            ++cnt[x];
        }
        sort(cnt, cnt + mx + 1, greater<int>());
        int ans = 0;
        int m = 0;
        for (int& x : cnt) {
            if (x) {
                m += x;
                ++ans;
                if (m * 2 >= arr.size()) {
                    break;
                }
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func minSetSize(arr []int) (ans int) {
	mx := slices.Max(arr)
	cnt := make([]int, mx+1)
	for _, x := range arr {
		cnt[x]++
	}
	sort.Ints(cnt)
	for i, m := mx, 0; ; i-- {
		if cnt[i] > 0 {
			m += cnt[i]
			ans++
			if m >= len(arr)/2 {
				return
			}
		}
	}
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function minSetSize(arr: number[]): number {
    const counter = new Map<number, number>();
    for (const v of arr) {
        counter.set(v, (counter.get(v) ?? 0) + 1);
    }
    const t = Array.from(counter.values());
    t.sort((a, b) => b - a);
    let ans = 0;
    let n = 0;
    for (const cnt of t) {
        n += cnt;
        ++ans;
        if (n * 2 >= arr.length) {
            break;
        }
    }
    return ans;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
