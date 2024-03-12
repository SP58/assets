---
title: Destination City
summary: Destination City - Solution Explained
url: "/posts/destination-city"
date: 2020-09-26T04:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Destination City LeetCode Solution Explained in all languages", "1436", "leetcode question 1436", "Destination City", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/destination-city.webp
    alt: Destination City - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1436. Destination City](https://leetcode.com/problems/destination-city)


## Description

<p>You are given the array <code>paths</code>, where <code>paths[i] = [cityA<sub>i</sub>, cityB<sub>i</sub>]</code> means there exists a direct path going from <code>cityA<sub>i</sub></code> to <code>cityB<sub>i</sub></code>. <em>Return the destination city, that is, the city without any path outgoing to another city.</em></p>

<p>It is guaranteed that the graph of paths forms a line without any loop, therefore, there will be exactly one destination city.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> paths = [[&quot;London&quot;,&quot;New York&quot;],[&quot;New York&quot;,&quot;Lima&quot;],[&quot;Lima&quot;,&quot;Sao Paulo&quot;]]
<strong>Output:</strong> &quot;Sao Paulo&quot; 
<strong>Explanation:</strong> Starting at &quot;London&quot; city you will reach &quot;Sao Paulo&quot; city which is the destination city. Your trip consist of: &quot;London&quot; -&gt; &quot;New York&quot; -&gt; &quot;Lima&quot; -&gt; &quot;Sao Paulo&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> paths = [[&quot;B&quot;,&quot;C&quot;],[&quot;D&quot;,&quot;B&quot;],[&quot;C&quot;,&quot;A&quot;]]
<strong>Output:</strong> &quot;A&quot;
<strong>Explanation:</strong> All possible trips are:&nbsp;
&quot;D&quot; -&gt; &quot;B&quot; -&gt; &quot;C&quot; -&gt; &quot;A&quot;.&nbsp;
&quot;B&quot; -&gt; &quot;C&quot; -&gt; &quot;A&quot;.&nbsp;
&quot;C&quot; -&gt; &quot;A&quot;.&nbsp;
&quot;A&quot;.&nbsp;
Clearly the destination city is &quot;A&quot;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> paths = [[&quot;A&quot;,&quot;Z&quot;]]
<strong>Output:</strong> &quot;Z&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= paths.length &lt;= 100</code></li>
	<li><code>paths[i].length == 2</code></li>
	<li><code>1 &lt;= cityA<sub>i</sub>.length, cityB<sub>i</sub>.length &lt;= 10</code></li>
	<li><code>cityA<sub>i</sub> != cityB<sub>i</sub></code></li>
	<li>All strings consist of lowercase and uppercase English letters and the space character.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def destCity(self, paths: List[List[str]]) -> str:
        s = {a for a, _ in paths}
        return next(b for _, b in paths if b not in s)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public String destCity(List<List<String>> paths) {
        Set<String> s = new HashSet<>();
        for (var p : paths) {
            s.add(p.get(0));
        }
        for (var p : paths) {
            if (!s.contains(p.get(1))) {
                return p.get(1);
            }
        }
        return "";
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    string destCity(vector<vector<string>>& paths) {
        unordered_set<string> s;
        for (auto& p : paths) {
            s.insert(p[0]);
        }
        for (auto& p : paths) {
            if (!s.count(p[1])) {
                return p[1];
            }
        }
        return "";
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func destCity(paths [][]string) string {
	s := map[string]bool{}
	for _, p := range paths {
		s[p[0]] = true
	}
	for _, p := range paths {
		if !s[p[1]] {
			return p[1]
		}
	}
	return ""
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function destCity(paths: string[][]): string {
    const set = new Set(paths.map(([a]) => a));
    for (const [_, b] of paths) {
        if (!set.has(b)) {
            return b;
        }
    }
    return '';
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
use std::collections::HashSet;
impl Solution {
    pub fn dest_city(paths: Vec<Vec<String>>) -> String {
        let set = paths
            .iter()
            .map(|v| &v[0])
            .collect::<HashSet<&String>>();
        for path in paths.iter() {
            if !set.contains(&path[1]) {
                return path[1].clone();
            }
        }
        String::new()
    }
}
```
{{< /terminal >}}

{{< terminal title="JavaScript Code" >}}
```js
/**
 * @param {string[][]} paths
 * @return {string}
 */
var destCity = function (paths) {
    const s = new Set();
    for (const [a, _] of paths) {
        s.add(a);
    }
    for (const [_, b] of paths) {
        if (!s.has(b)) {
            return b;
        }
    }
    return '';
};
```
{{< /terminal >}}

{{< terminal title="C Code" >}}
```c
char* destCity(char*** paths, int pathsSize, int* pathsColSize) {
    for (int i = 0; i < pathsSize; i++) {
        int flag = 1;
        for (int j = 0; j < pathsSize; j++) {
            if (strcmp(paths[i][1], paths[j][0]) == 0) {
                flag = 0;
                break;
            }
        }
        if (flag) {
            return paths[i][1];
        }
    }
    return NULL;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
