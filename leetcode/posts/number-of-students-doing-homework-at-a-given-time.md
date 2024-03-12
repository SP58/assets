---
title: Number of Students Doing Homework at a Given Time
summary: Number of Students Doing Homework at a Given Time - Solution Explained
url: "/posts/number-of-students-doing-homework-at-a-given-time"
date: 2020-09-25T14:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Number of Students Doing Homework at a Given Time LeetCode Solution Explained in all languages", "1450", "leetcode question 1450", "Number of Students Doing Homework at a Given Time", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/number-of-students-doing-homework-at-a-given-time.webp
    alt: Number of Students Doing Homework at a Given Time - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1450. Number of Students Doing Homework at a Given Time](https://leetcode.com/problems/number-of-students-doing-homework-at-a-given-time)


## Description

<p>Given two integer arrays <code>startTime</code> and <code>endTime</code> and given an integer <code>queryTime</code>.</p>

<p>The <code>ith</code> student started doing their homework at the time <code>startTime[i]</code> and finished it at time <code>endTime[i]</code>.</p>

<p>Return <em>the number of students</em> doing their homework at time <code>queryTime</code>. More formally, return the number of students where <code>queryTime</code> lays in the interval <code>[startTime[i], endTime[i]]</code> inclusive.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> startTime = [1,2,3], endTime = [3,2,7], queryTime = 4
<strong>Output:</strong> 1
<strong>Explanation:</strong> We have 3 students where:
The first student started doing homework at time 1 and finished at time 3 and wasn&#39;t doing anything at time 4.
The second student started doing homework at time 2 and finished at time 2 and also wasn&#39;t doing anything at time 4.
The third student started doing homework at time 3 and finished at time 7 and was the only student doing homework at time 4.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> startTime = [4], endTime = [4], queryTime = 4
<strong>Output:</strong> 1
<strong>Explanation:</strong> The only student was doing their homework at the queryTime.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>startTime.length == endTime.length</code></li>
	<li><code>1 &lt;= startTime.length &lt;= 100</code></li>
	<li><code>1 &lt;= startTime[i] &lt;= endTime[i] &lt;= 1000</code></li>
	<li><code>1 &lt;= queryTime &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def busyStudent(
        self, startTime: List[int], endTime: List[int], queryTime: int
    ) -> int:
        return sum(a <= queryTime <= b for a, b in zip(startTime, endTime))
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int busyStudent(int[] startTime, int[] endTime, int queryTime) {
        int ans = 0;
        for (int i = 0; i < startTime.length; ++i) {
            if (startTime[i] <= queryTime && queryTime <= endTime[i]) {
                ++ans;
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
    int busyStudent(vector<int>& startTime, vector<int>& endTime, int queryTime) {
        int ans = 0;
        for (int i = 0; i < startTime.size(); ++i) {
            ans += startTime[i] <= queryTime && queryTime <= endTime[i];
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func busyStudent(startTime []int, endTime []int, queryTime int) int {
	ans := 0
	for i, a := range startTime {
		b := endTime[i]
		if a <= queryTime && queryTime <= b {
			ans++
		}
	}
	return ans
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function busyStudent(startTime: number[], endTime: number[], queryTime: number): number {
    const n = startTime.length;
    let res = 0;
    for (let i = 0; i < n; i++) {
        if (startTime[i] <= queryTime && endTime[i] >= queryTime) {
            res++;
        }
    }
    return res;
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn busy_student(start_time: Vec<i32>, end_time: Vec<i32>, query_time: i32) -> i32 {
        let mut res = 0;
        for i in 0..start_time.len() {
            if start_time[i] <= query_time && end_time[i] >= query_time {
                res += 1;
            }
        }
        res
    }
}
```
{{< /terminal >}}

{{< terminal title="C Code" >}}
```c
int busyStudent(int* startTime, int startTimeSize, int* endTime, int endTimeSize, int queryTime) {
    int res = 0;
    for (int i = 0; i < startTimeSize; i++) {
        if (startTime[i] <= queryTime && endTime[i] >= queryTime) {
            res++;
        }
    }
    return res;
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def busyStudent(
        self, startTime: List[int], endTime: List[int], queryTime: int
    ) -> int:
        c = [0] * 1010
        for a, b in zip(startTime, endTime):
            c[a] += 1
            c[b + 1] -= 1
        return sum(c[: queryTime + 1])
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int busyStudent(int[] startTime, int[] endTime, int queryTime) {
        int[] c = new int[1010];
        for (int i = 0; i < startTime.length; ++i) {
            c[startTime[i]]++;
            c[endTime[i] + 1]--;
        }
        int ans = 0;
        for (int i = 0; i <= queryTime; ++i) {
            ans += c[i];
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
    int busyStudent(vector<int>& startTime, vector<int>& endTime, int queryTime) {
        vector<int> c(1010);
        for (int i = 0; i < startTime.size(); ++i) {
            c[startTime[i]]++;
            c[endTime[i] + 1]--;
        }
        int ans = 0;
        for (int i = 0; i <= queryTime; ++i) {
            ans += c[i];
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func busyStudent(startTime []int, endTime []int, queryTime int) int {
	c := make([]int, 1010)
	for i, a := range startTime {
		b := endTime[i]
		c[a]++
		c[b+1]--
	}
	ans := 0
	for i := 0; i <= queryTime; i++ {
		ans += c[i]
	}
	return ans
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
