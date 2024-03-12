---
title: Minimum Deletions to Make Character Frequencies Unique
summary: Minimum Deletions to Make Character Frequencies Unique - Solution Explained
url: "/posts/minimum-deletions-to-make-character-frequencies-unique"
date: 2020-09-17T09:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Minimum Deletions to Make Character Frequencies Unique LeetCode Solution Explained in all languages", "1647", "leetcode question 1647", "Minimum Deletions to Make Character Frequencies Unique", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/minimum-deletions-to-make-character-frequencies-unique.webp
    alt: Minimum Deletions to Make Character Frequencies Unique - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1647. Minimum Deletions to Make Character Frequencies Unique](https://leetcode.com/problems/minimum-deletions-to-make-character-frequencies-unique)


## Description

<p>A string <code>s</code> is called <strong>good</strong> if there are no two different characters in <code>s</code> that have the same <strong>frequency</strong>.</p>

<p>Given a string <code>s</code>, return<em> the <strong>minimum</strong> number of characters you need to delete to make </em><code>s</code><em> <strong>good</strong>.</em></p>

<p>The <strong>frequency</strong> of a character in a string is the number of times it appears in the string. For example, in the string <code>&quot;aab&quot;</code>, the <strong>frequency</strong> of <code>&#39;a&#39;</code> is <code>2</code>, while the <strong>frequency</strong> of <code>&#39;b&#39;</code> is <code>1</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aab&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> <code>s</code> is already good.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aaabbbcc&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> You can delete two &#39;b&#39;s resulting in the good string &quot;aaabcc&quot;.
Another way it to delete one &#39;b&#39; and one &#39;c&#39; resulting in the good string &quot;aaabbc&quot;.</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ceabaacb&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> You can delete both &#39;c&#39;s resulting in the good string &quot;eabaab&quot;.
Note that we only care about characters that are still in the string at the end (i.e. frequency of 0 is ignored).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code>&nbsp;contains only lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def minDeletions(self, s: str) -> int:
        cnt = Counter(s)
        ans, pre = 0, inf
        for v in sorted(cnt.values(), reverse=True):
            if pre == 0:
                ans += v
            elif v >= pre:
                ans += v - pre + 1
                pre -= 1
            else:
                pre = v
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int minDeletions(String s) {
        int[] cnt = new int[26];
        for (int i = 0; i < s.length(); ++i) {
            ++cnt[s.charAt(i) - 'a'];
        }
        Arrays.sort(cnt);
        int ans = 0;
        for (int i = 24; i >= 0; --i) {
            while (cnt[i] >= cnt[i + 1] && cnt[i] > 0) {
                --cnt[i];
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
    int minDeletions(string s) {
        vector<int> cnt(26);
        for (char& c : s) ++cnt[c - 'a'];
        sort(cnt.rbegin(), cnt.rend());
        int ans = 0;
        for (int i = 1; i < 26; ++i) {
            while (cnt[i] >= cnt[i - 1] && cnt[i] > 0) {
                --cnt[i];
                ++ans;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func minDeletions(s string) (ans int) {
	cnt := make([]int, 26)
	for _, c := range s {
		cnt[c-'a']++
	}
	sort.Sort(sort.Reverse(sort.IntSlice(cnt)))
	for i := 1; i < 26; i++ {
		for cnt[i] >= cnt[i-1] && cnt[i] > 0 {
			cnt[i]--
			ans++
		}
	}
	return
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function minDeletions(s: string): number {
    let map = {};
    for (let c of s) {
        map[c] = (map[c] || 0) + 1;
    }
    let ans = 0;
    let vals: number[] = Object.values(map);
    vals.sort((a, b) => a - b);
    for (let i = 1; i < vals.length; ++i) {
        while (vals[i] > 0 && i != vals.indexOf(vals[i])) {
            --vals[i];
            ++ans;
        }
    }
    return ans;
}
```
{{< /terminal >}}

{{< terminal title="Rust Code" >}}
```rust
impl Solution {
    #[allow(dead_code)]
    pub fn min_deletions(s: String) -> i32 {
        let mut cnt = vec![0; 26];
        let mut ans = 0;

        for c in s.chars() {
            cnt[((c as u8) - ('a' as u8)) as usize] += 1;
        }

        cnt.sort_by(|&lhs, &rhs| { rhs.cmp(&lhs) });

        for i in 1..26 {
            while cnt[i] >= cnt[i - 1] && cnt[i] > 0 {
                cnt[i] -= 1;
                ans += 1;
            }
        }

        ans
    }
}
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def minDeletions(self, s: str) -> int:
        cnt = Counter(s)
        vals = sorted(cnt.values(), reverse=True)
        ans = 0
        for i in range(1, len(vals)):
            while vals[i] >= vals[i - 1] and vals[i] > 0:
                vals[i] -= 1
                ans += 1
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    public int minDeletions(String s) {
        int[] cnt = new int[26];
        for (int i = 0; i < s.length(); ++i) {
            ++cnt[s.charAt(i) - 'a'];
        }
        Arrays.sort(cnt);
        int ans = 0, pre = 1 << 30;
        for (int i = 25; i >= 0; --i) {
            int v = cnt[i];
            if (pre == 0) {
                ans += v;
            } else if (v >= pre) {
                ans += v - pre + 1;
                --pre;
            } else {
                pre = v;
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
    int minDeletions(string s) {
        vector<int> cnt(26);
        for (char& c : s) ++cnt[c - 'a'];
        sort(cnt.rbegin(), cnt.rend());
        int ans = 0, pre = 1 << 30;
        for (int& v : cnt) {
            if (pre == 0) {
                ans += v;
            } else if (v >= pre) {
                ans += v - pre + 1;
                --pre;
            } else {
                pre = v;
            }
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func minDeletions(s string) (ans int) {
	cnt := make([]int, 26)
	for _, c := range s {
		cnt[c-'a']++
	}
	sort.Sort(sort.Reverse(sort.IntSlice(cnt)))
	pre := 1 << 30
	for _, v := range cnt {
		if pre == 0 {
			ans += v
		} else if v >= pre {
			ans += v - pre + 1
			pre--
		} else {
			pre = v
		}
	}
	return
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
