---
title: Defanging an IP Address
summary: Defanging an IP Address - Solution Explained
url: "/posts/defanging-an-ip-address"
date: 2020-10-09T20:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Defanging an IP Address LeetCode Solution Explained in all languages", "1108", "leetcode question 1108", "Defanging an IP Address", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/defanging-an-ip-address.webp
    alt: Defanging an IP Address - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1108. Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address)


## Description

<p>Given a valid (IPv4) IP <code>address</code>, return a defanged version of that IP address.</p>

<p>A <em>defanged&nbsp;IP address</em>&nbsp;replaces every period <code>&quot;.&quot;</code> with <code>&quot;[.]&quot;</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> address = "1.1.1.1"
<strong>Output:</strong> "1[.]1[.]1[.]1"
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> address = "255.100.50.0"
<strong>Output:</strong> "255[.]100[.]50[.]0"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The given <code>address</code> is a valid IPv4 address.</li>
</ul>

## Solutions

### Solution 1: Direct Replacement

We can directly replace the `'.'` in the string with `'[.]'`.

The time complexity is $O(n)$, where $n$ is the length of the string. Ignoring the space consumption of the answer, the space complexity is $O(1)$.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def defangIPaddr(self, address: str) -> str:
        return address.replace('.', '[.]')
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public String defangIPaddr(String address) {
        return address.replace(".", "[.]");
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    string defangIPaddr(string address) {
        for (int i = address.size(); i >= 0; --i) {
            if (address[i] == '.') {
                address.replace(i, 1, "[.]");
            }
        }
        return address;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func defangIPaddr(address string) string {
	return strings.Replace(address, ".", "[.]", -1)
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function defangIPaddr(address: string): string {
    return address.split('.').join('[.]');
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
