---
title: Count the Number of Good Subsequences
summary: Count the Number of Good Subsequences - Solution Explained
url: "/posts/count-the-number-of-good-subsequences"
date: 2020-08-11T05:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Count the Number of Good Subsequences LeetCode Solution Explained in all languages", "2539", "leetcode question 2539", "Count the Number of Good Subsequences", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/count-the-number-of-good-subsequences.webp
    alt: Count the Number of Good Subsequences - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2539. Count the Number of Good Subsequences](https://leetcode.com/problems/count-the-number-of-good-subsequences)


## Description

<p>A <strong>subsequence</strong> of a string is&nbsp;good if it is not empty and the frequency of each one of its characters is the same.</p>

<p>Given a string <code>s</code>, return <em>the number of good subsequences of</em> <code>s</code>. Since the answer may be too large, return it modulo <code>10<sup>9</sup> + 7</code>.</p>

<p>A <strong>subsequence</strong> is a string that can be derived from another string by deleting some or no characters without changing the order of the remaining characters.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aabb&quot;
<strong>Output:</strong> 11
<strong>Explanation:</strong> The total number of subsequences is <code>2<sup>4</sup>. </code>There are five subsequences which are not good: &quot;<strong><u>aab</u></strong>b&quot;, &quot;a<u><strong>abb</strong></u>&quot;, &quot;<strong><u>a</u></strong>a<u><strong>bb</strong></u>&quot;, &quot;<u><strong>aa</strong></u>b<strong><u>b</u></strong>&quot;, and the empty subsequence. Hence, the number of good subsequences is <code>2<sup>4</sup>-5 = 11</code>.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leet&quot;
<strong>Output:</strong> 12
<strong>Explanation:</strong> There are four subsequences which are not good: &quot;<strong><u>l</u><em>ee</em></strong>t&quot;, &quot;l<u><strong>eet</strong></u>&quot;, &quot;<strong><u>leet</u></strong>&quot;, and the empty subsequence. Hence, the number of good subsequences is <code>2<sup>4</sup>-4 = 12</code>.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcd&quot;
<strong>Output:</strong> 15
<strong>Explanation:</strong> All of the non-empty subsequences are good subsequences. Hence, the number of good subsequences is <code>2<sup>4</sup>-1 = 15</code>.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
N = 10001
MOD = 10**9 + 7
f = [1] * N
g = [1] * N
for i in range(1, N):
    f[i] = f[i - 1] * i % MOD
    g[i] = pow(f[i], MOD - 2, MOD)


def comb(n, k):
    return f[n] * g[k] * g[n - k] % MOD


class Solution:
    def countGoodSubsequences(self, s: str) -> int:
        cnt = Counter(s)
        ans = 0
        for i in range(1, max(cnt.values()) + 1):
            x = 1
            for v in cnt.values():
                if v >= i:
                    x = x * (comb(v, i) + 1) % MOD
            ans = (ans + x - 1) % MOD
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    private static final int N = 10001;
    private static final int MOD = (int) 1e9 + 7;
    private static final long[] F = new long[N];
    private static final long[] G = new long[N];

    static {
        F[0] = 1;
        G[0] = 1;
        for (int i = 1; i < N; ++i) {
            F[i] = F[i - 1] * i % MOD;
            G[i] = qmi(F[i], MOD - 2, MOD);
        }
    }

    public static long qmi(long a, long k, long p) {
        long res = 1;
        while (k != 0) {
            if ((k & 1) == 1) {
                res = res * a % p;
            }
            k >>= 1;
            a = a * a % p;
        }
        return res;
    }

    public static long comb(int n, int k) {
        return (F[n] * G[k] % MOD) * G[n - k] % MOD;
    }

    public int countGoodSubsequences(String s) {
        int[] cnt = new int[26];
        int mx = 1;
        for (int i = 0; i < s.length(); ++i) {
            mx = Math.max(mx, ++cnt[s.charAt(i) - 'a']);
        }
        long ans = 0;
        for (int i = 1; i <= mx; ++i) {
            long x = 1;
            for (int j = 0; j < 26; ++j) {
                if (cnt[j] >= i) {
                    x = x * (comb(cnt[j], i) + 1) % MOD;
                }
            }
            ans = (ans + x - 1) % MOD;
        }
        return (int) ans;
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
int N = 10001;
int MOD = 1e9 + 7;
long f[10001];
long g[10001];

long qmi(long a, long k, long p) {
    long res = 1;
    while (k != 0) {
        if ((k & 1) == 1) {
            res = res * a % p;
        }
        k >>= 1;
        a = a * a % p;
    }
    return res;
}

int init = []() {
    f[0] = 1;
    g[0] = 1;
    for (int i = 1; i < N; ++i) {
        f[i] = f[i - 1] * i % MOD;
        g[i] = qmi(f[i], MOD - 2, MOD);
    }
    return 0;
}();

int comb(int n, int k) {
    return (f[n] * g[k] % MOD) * g[n - k] % MOD;
}

class Solution {
public:
    int countGoodSubsequences(string s) {
        int cnt[26]{};
        int mx = 1;
        for (char& c : s) {
            mx = max(mx, ++cnt[c - 'a']);
        }
        long ans = 0;
        for (int i = 1; i <= mx; ++i) {
            long x = 1;
            for (int j = 0; j < 26; ++j) {
                if (cnt[j] >= i) {
                    x = (x * (comb(cnt[j], i) + 1)) % MOD;
                }
            }
            ans = (ans + x - 1) % MOD;
        }
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
const n = 1e4 + 1
const mod = 1e9 + 7

var f = make([]int, n)
var g = make([]int, n)

func qmi(a, k, p int) int {
	res := 1
	for k != 0 {
		if k&1 == 1 {
			res = res * a % p
		}
		k >>= 1
		a = a * a % p
	}
	return res
}

func init() {
	f[0], g[0] = 1, 1
	for i := 1; i < n; i++ {
		f[i] = f[i-1] * i % mod
		g[i] = qmi(f[i], mod-2, mod)
	}
}

func comb(n, k int) int {
	return (f[n] * g[k] % mod) * g[n-k] % mod
}

func countGoodSubsequences(s string) (ans int) {
	cnt := [26]int{}
	mx := 1
	for _, c := range s {
		cnt[c-'a']++
		mx = max(mx, cnt[c-'a'])
	}
	for i := 1; i <= mx; i++ {
		x := 1
		for _, v := range cnt {
			if v >= i {
				x = (x * (comb(v, i) + 1)) % mod
			}
		}
		ans = (ans + x - 1) % mod
	}
	return
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->