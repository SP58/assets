---
title: Count Paths That Can Form a Palindrome in a Tree
summary: Count Paths That Can Form a Palindrome in a Tree - Solution Explained
url: "/posts/count-paths-that-can-form-a-palindrome-in-a-tree"
date: 2020-07-31T17:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Count Paths That Can Form a Palindrome in a Tree LeetCode Solution Explained in all languages", "2791", "leetcode question 2791", "Count Paths That Can Form a Palindrome in a Tree", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/count-paths-that-can-form-a-palindrome-in-a-tree.webp
    alt: Count Paths That Can Form a Palindrome in a Tree - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2791. Count Paths That Can Form a Palindrome in a Tree](https://leetcode.com/problems/count-paths-that-can-form-a-palindrome-in-a-tree)


## Description

<p>You are given a <strong>tree</strong> (i.e. a connected, undirected graph that has no cycles) <strong>rooted</strong> at node <code>0</code> consisting of <code>n</code> nodes numbered from <code>0</code> to <code>n - 1</code>. The tree is represented by a <strong>0-indexed</strong> array <code>parent</code> of size <code>n</code>, where <code>parent[i]</code> is the parent of node <code>i</code>. Since node <code>0</code> is the root, <code>parent[0] == -1</code>.</p>

<p>You are also given a string <code>s</code> of length <code>n</code>, where <code>s[i]</code> is the character assigned to the edge between <code>i</code> and <code>parent[i]</code>. <code>s[0]</code> can be ignored.</p>

<p>Return <em>the number of pairs of nodes </em><code>(u, v)</code><em> such that </em><code>u &lt; v</code><em> and the characters assigned to edges on the path from </em><code>u</code><em> to </em><code>v</code><em> can be <strong>rearranged</strong> to form a <strong>palindrome</strong></em>.</p>

<p>A string is a <strong>palindrome</strong> when it reads the same backwards as forwards.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<p><img alt="" src="https://spcdn.pages.dev/leetcode/problems/2791.Count%20Paths%20That%20Can%20Form%20a%20Palindrome%20in%20a%20Tree/images/treedrawio-8drawio.png" style="width: 281px; height: 181px;" /></p>

<pre>
<strong>Input:</strong> parent = [-1,0,0,1,1,2], s = &quot;acaabc&quot;
<strong>Output:</strong> 8
<strong>Explanation:</strong> The valid pairs are:
- All the pairs (0,1), (0,2), (1,3), (1,4) and (2,5) result in one character which is always a palindrome.
- The pair (2,3) result in the string &quot;aca&quot; which is a palindrome.
- The pair (1,5) result in the string &quot;cac&quot; which is a palindrome.
- The pair (3,5) result in the string &quot;acac&quot; which can be rearranged into the palindrome &quot;acca&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> parent = [-1,0,0,0,0], s = &quot;aaaaa&quot;
<strong>Output:</strong> 10
<strong>Explanation:</strong> Any pair of nodes (u,v) where u &lt; v is valid.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == parent.length == s.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= parent[i] &lt;= n - 1</code> for all <code>i &gt;= 1</code></li>
	<li><code>parent[0] == -1</code></li>
	<li><code>parent</code> represents a valid tree.</li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class Solution:
    def countPalindromePaths(self, parent: List[int], s: str) -> int:
        def dfs(i: int, xor: int):
            nonlocal ans
            for j, v in g[i]:
                x = xor ^ v
                ans += cnt[x]
                for k in range(26):
                    ans += cnt[x ^ (1 << k)]
                cnt[x] += 1
                dfs(j, x)

        n = len(parent)
        g = defaultdict(list)
        for i in range(1, n):
            p = parent[i]
            g[p].append((i, 1 << (ord(s[i]) - ord('a'))))
        ans = 0
        cnt = Counter({0: 1})
        dfs(0, 0)
        return ans
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class Solution {
    private List<int[]>[] g;
    private Map<Integer, Integer> cnt = new HashMap<>();
    private long ans;

    public long countPalindromePaths(List<Integer> parent, String s) {
        int n = parent.size();
        g = new List[n];
        cnt.put(0, 1);
        Arrays.setAll(g, k -> new ArrayList<>());
        for (int i = 1; i < n; ++i) {
            int p = parent.get(i);
            g[p].add(new int[] {i, 1 << (s.charAt(i) - 'a')});
        }
        dfs(0, 0);
        return ans;
    }

    private void dfs(int i, int xor) {
        for (int[] e : g[i]) {
            int j = e[0], v = e[1];
            int x = xor ^ v;
            ans += cnt.getOrDefault(x, 0);
            for (int k = 0; k < 26; ++k) {
                ans += cnt.getOrDefault(x ^ (1 << k), 0);
            }
            cnt.merge(x, 1, Integer::sum);
            dfs(j, x);
        }
    }
}
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class Solution {
public:
    long long countPalindromePaths(vector<int>& parent, string s) {
        int n = parent.size();
        vector<vector<pair<int, int>>> g(n);
        unordered_map<int, int> cnt;
        cnt[0] = 1;
        for (int i = 1; i < n; ++i) {
            int p = parent[i];
            g[p].emplace_back(i, 1 << (s[i] - 'a'));
        }
        long long ans = 0;
        function<void(int, int)> dfs = [&](int i, int xo) {
            for (auto [j, v] : g[i]) {
                int x = xo ^ v;
                ans += cnt[x];
                for (int k = 0; k < 26; ++k) {
                    ans += cnt[x ^ (1 << k)];
                }
                ++cnt[x];
                dfs(j, x);
            }
        };
        dfs(0, 0);
        return ans;
    }
};
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
func countPalindromePaths(parent []int, s string) (ans int64) {
	type pair struct{ i, v int }
	n := len(parent)
	g := make([][]pair, n)
	for i := 1; i < n; i++ {
		p := parent[i]
		g[p] = append(g[p], pair{i, 1 << (s[i] - 'a')})
	}
	cnt := map[int]int{0: 1}
	var dfs func(i, xor int)
	dfs = func(i, xor int) {
		for _, e := range g[i] {
			x := xor ^ e.v
			ans += int64(cnt[x])
			for k := 0; k < 26; k++ {
				ans += int64(cnt[x^(1<<k)])
			}
			cnt[x]++
			dfs(e.i, x)
		}
	}
	dfs(0, 0)
	return
}
```
{{< /terminal >}}

{{< terminal title="TypeScript Code" >}}
```ts
function countPalindromePaths(parent: number[], s: string): number {
    const n = parent.length;
    const g: [number, number][][] = Array.from({ length: n }, () => []);
    for (let i = 1; i < n; ++i) {
        g[parent[i]].push([i, 1 << (s.charCodeAt(i) - 97)]);
    }
    const cnt: Map<number, number> = new Map();
    cnt.set(0, 1);
    let ans = 0;
    const dfs = (i: number, xor: number): void => {
        for (const [j, v] of g[i]) {
            const x = xor ^ v;
            ans += cnt.get(x) || 0;
            for (let k = 0; k < 26; ++k) {
                ans += cnt.get(x ^ (1 << k)) || 0;
            }
            cnt.set(x, (cnt.get(x) || 0) + 1);
            dfs(j, x);
        }
    };
    dfs(0, 0);
    return ans;
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->