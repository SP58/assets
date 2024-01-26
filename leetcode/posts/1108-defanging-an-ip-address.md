---
title: 1108 Defanging an IP Address
summary: 1108 Defanging an IP Address LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1108 Defanging an IP Address LeetCode Solution Explained in all languages", "1108 Defanging an IP Address", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1108 Defanging an IP Address - Solution Explained/problem-solving.webp
    alt: 1108 Defanging an IP Address
    hiddenInList: true
    hiddenInSingle: false
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

```python
class Solution:
    def defangIPaddr(self, address: str) -> str:
        return address.replace('.', '[.]')
```

```java
class Solution {
    public String defangIPaddr(String address) {
        return address.replace(".", "[.]");
    }
}
```

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

```go
func defangIPaddr(address string) string {
	return strings.Replace(address, ".", "[.]", -1)
}
```

```ts
function defangIPaddr(address: string): string {
    return address.split('.').join('[.]');
}
```

<!-- tabs:end -->

<!-- end -->
