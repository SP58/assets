---
title: Determine if Two Events Have Conflict
summary: Determine if Two Events Have Conflict - Solution Explained
url: "/posts/determine-if-two-events-have-conflict"
date: 2020-08-15T02:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Determine if Two Events Have Conflict LeetCode Solution Explained in all languages", "2446", "leetcode question 2446", "Determine if Two Events Have Conflict", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/determine-if-two-events-have-conflict.webp
    alt: Determine if Two Events Have Conflict - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2446. Determine if Two Events Have Conflict](https://leetcode.com/problems/determine-if-two-events-have-conflict)


## Description

<p>You are given two arrays of strings that represent two inclusive events that happened <strong>on the same day</strong>, <code>event1</code> and <code>event2</code>, where:</p>

<ul>
	<li><code>event1 = [startTime<sub>1</sub>, endTime<sub>1</sub>]</code> and</li>
	<li><code>event2 = [startTime<sub>2</sub>, endTime<sub>2</sub>]</code>.</li>
</ul>

<p>Event times are valid 24 hours format in the form of <code>HH:MM</code>.</p>

<p>A <strong>conflict</strong> happens when two events have some non-empty intersection (i.e., some moment is common to both events).</p>

<p>Return <code>true</code><em> if there is a conflict between two events. Otherwise, return </em><code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> event1 = [&quot;01:15&quot;,&quot;02:00&quot;], event2 = [&quot;02:00&quot;,&quot;03:00&quot;]
<strong>Output:</strong> true
<strong>Explanation:</strong> The two events intersect at time 2:00.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> event1 = [&quot;01:00&quot;,&quot;02:00&quot;], event2 = [&quot;01:20&quot;,&quot;03:00&quot;]
<strong>Output:</strong> true
<strong>Explanation:</strong> The two events intersect starting from 01:20 to 02:00.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> event1 = [&quot;10:00&quot;,&quot;11:00&quot;], event2 = [&quot;14:00&quot;,&quot;15:00&quot;]
<strong>Output:</strong> false
<strong>Explanation:</strong> The two events do not intersect.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>evnet1.length == event2.length == 2.</code></li>
	<li><code>event1[i].length == event2[i].length == 5</code></li>
	<li><code>startTime<sub>1</sub> &lt;= endTime<sub>1</sub></code></li>
	<li><code>startTime<sub>2</sub> &lt;= endTime<sub>2</sub></code></li>
	<li>All the event times follow the <code>HH:MM</code> format.</li>
</ul>

## Solutions

### Solution 1: String Comparison

If the start time of $event1$ is later than the end time of $event2$, or the end time of $event1$ is earlier than the start time of $event2$, then the two events will not conflict. Otherwise, the two events will conflict.

<img alt="" src="https://spcdn.pages.dev/leetcode/problems/2446.Determine%20if%20Two%20Events%20Have%20Conflict/images/event.png" />

The time complexity is $O(1)$, and the space complexity is $O(1)$.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def haveConflict(self, event1: List[str], event2: List[str]) -> bool:
        return not (event1[0] > event2[1] or event1[1] < event2[0])
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public boolean haveConflict(String[] event1, String[] event2) {
        return !(event1[0].compareTo(event2[1]) > 0 || event1[1].compareTo(event2[0]) < 0);
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    bool haveConflict(vector<string>& event1, vector<string>& event2) {
        return !(event1[0] > event2[1] || event1[1] < event2[0]);
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func haveConflict(event1 []string, event2 []string) bool {
	return !(event1[0] > event2[1] || event1[1] < event2[0])
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function haveConflict(event1: string[], event2: string[]): boolean {
    return !(event1[0] > event2[1] || event1[1] < event2[0]);
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    pub fn have_conflict(event1: Vec<String>, event2: Vec<String>) -> bool {
        !(event1[1] < event2[0] || event1[0] > event2[1])
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
