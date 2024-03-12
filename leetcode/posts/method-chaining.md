---
title: Method Chaining
summary: Method Chaining - Solution Explained
url: "/posts/method-chaining"
date: 2020-07-27T13:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Method Chaining LeetCode Solution Explained in all languages", "2891", "leetcode question 2891", "Method Chaining", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/method-chaining.webp
    alt: Method Chaining - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2891. Method Chaining](https://leetcode.com/problems/method-chaining)


## Description

<pre>
DataFrame <code>animals</code>
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| name        | object |
| species     | object |
| age         | int    |
| weight      | int    |
+-------------+--------+
</pre>

<p>Write a solution to list the names of animals that weigh <strong>strictly more than</strong> <code>100</code> kilograms.</p>

<p>Return the&nbsp;animals sorted by weight in <strong>descending order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
DataFrame animals:
+----------+---------+-----+--------+
| name     | species | age | weight |
+----------+---------+-----+--------+
| Tatiana  | Snake   | 98  | 464    |
| Khaled   | Giraffe | 50  | 41     |
| Alex     | Leopard | 6   | 328    |
| Jonathan | Monkey  | 45  | 463    |
| Stefan   | Bear    | 100 | 50     |
| Tommy    | Panda   | 26  | 349    |
+----------+---------+-----+--------+
<strong>Output:</strong> 
+----------+
| name     |
+----------+
| Tatiana  |
| Jonathan |
| Tommy    |
| Alex     |
+----------+
<strong>Explanation:</strong> 
All animals weighing more than 100 should be included in the results table.
Tatiana&#39;s weight is 464, Jonathan&#39;s weight is 463, Tommy&#39;s weight is 349, and Alex&#39;s weight is 328.
The results should be sorted in descending order of weight.</pre>

<p>&nbsp;</p>
<p>In Pandas, <strong>method chaining</strong> enables us to&nbsp;perform operations on a DataFrame without breaking up each operation into a separate line or creating multiple temporary variables.&nbsp;</p>

<p>Can you complete this&nbsp;task in just <strong>one line </strong>of code using method chaining?</p>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
import pandas as pd


def findHeavyAnimals(animals: pd.DataFrame) -> pd.DataFrame:
    return animals[animals['weight'] > 100].sort_values('weight', ascending=False)[
        ['name']
    ]
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
