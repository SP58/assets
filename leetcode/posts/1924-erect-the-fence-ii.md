---
title: 1924 Erect The Fence Ii
summary: 1924 Erect The Fence Ii LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1924 Erect The Fence Ii LeetCode Solution Explained in all languages", "1924 Erect The Fence Ii", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1924 Erect The Fence Ii - Solution Explained/problem-solving.webp
    alt: 1924 Erect The Fence Ii
    hiddenInList: true
    hiddenInSingle: false
---


# [1924. Erect the Fence II](https://leetcode.com/problems/erect-the-fence-ii)


## Description

<p>You are given a 2D integer array <code>trees</code> where <code>trees[i] = [x<sub>i</sub>, y<sub>i</sub>]</code> represents the location of the <code>i<sup>th</sup></code> tree in the garden.</p>

<p>You are asked to fence the entire garden using the minimum length of rope possible. The garden is well-fenced only if <strong>all the trees are enclosed</strong> and the rope used <strong>forms a perfect circle</strong>. A tree is considered enclosed if it is inside or on the border of the circle.</p>

<p>More formally, you must form a circle using the rope with a center <code>(x, y)</code> and radius <code>r</code> where all trees lie inside or on the circle and <code>r</code> is <strong>minimum</strong>.</p>

<p>Return <em>the center and radius of the circle as a length 3 array </em><code>[x, y, r]</code><em>.</em>&nbsp;Answers within <code>10<sup>-5</sup></code> of the actual answer will be accepted.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<p><strong><img alt="" src="https://spcdn.pages.dev/leetcode/problems/1924.Erect%20the%20Fence%20II/images/trees1.png" style="width: 510px; height: 501px;" /></strong></p>

<pre>
<strong>Input:</strong> trees = [[1,1],[2,2],[2,0],[2,4],[3,3],[4,2]]
<strong>Output:</strong> [2.00000,2.00000,2.00000]
<strong>Explanation:</strong> The fence will have center = (2, 2) and radius = 2
</pre>

<p><strong class="example">Example 2:</strong></p>

<p><strong><img alt="" src="https://spcdn.pages.dev/leetcode/problems/1924.Erect%20the%20Fence%20II/images/trees2.png" style="width: 510px; height: 501px;" /></strong></p>

<pre>
<strong>Input:</strong> trees = [[1,2],[2,2],[4,2]]
<strong>Output:</strong> [2.50000,2.00000,1.50000]
<strong>Explanation:</strong> The fence will have center = (2.5, 2) and radius = 1.5
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= trees.length &lt;= 3000</code></li>
	<li><code>trees[i].length == 2</code></li>
	<li><code>0 &lt;= x<sub>i</sub>, y<sub>i</sub> &lt;= 3000</code></li>
</ul>

## Solutions

<!-- end -->
