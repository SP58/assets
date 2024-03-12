---
title: Reshape Data Pivot
summary: Reshape Data Pivot - Solution Explained
url: "/posts/reshape-data-pivot"
date: 2020-07-27T15:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Reshape Data Pivot LeetCode Solution Explained in all languages", "2889", "leetcode question 2889", "Reshape Data Pivot", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/reshape-data-pivot.webp
    alt: Reshape Data Pivot - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2889. Reshape Data Pivot](https://leetcode.com/problems/reshape-data-pivot)


## Description

<pre>
DataFrame <code>weather</code>
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| city        | object |
| month       | object |
| temperature | int    |
+-------------+--------+
</pre>

<p>Write a solution to <strong>pivot</strong> the data so that each row represents temperatures for a specific month, and each city is a separate column.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<pre>
<strong class="example">Example 1:</strong>
<strong>Input:</strong>
+--------------+----------+-------------+
| city         | month    | temperature |
+--------------+----------+-------------+
| Jacksonville | January  | 13          |
| Jacksonville | February | 23          |
| Jacksonville | March    | 38          |
| Jacksonville | April    | 5           |
| Jacksonville | May      | 34          |
| ElPaso       | January  | 20          |
| ElPaso       | February | 6           |
| ElPaso       | March    | 26          |
| ElPaso       | April    | 2           |
| ElPaso       | May      | 43          |
+--------------+----------+-------------+
<strong>Output:</strong><code>
+----------+--------+--------------+
| month    | ElPaso | Jacksonville |
+----------+--------+--------------+
| April    | 2      | 5            |
| February | 6      | 23           |
| January  | 20     | 13           |
| March    | 26     | 38           |
| May      | 43     | 34           |
+----------+--------+--------------+</code>
<strong>Explanation:
</strong>The table is pivoted, each column represents a city, and each row represents a specific month.</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
import pandas as pd


def pivotTable(weather: pd.DataFrame) -> pd.DataFrame:
    return weather.pivot(index='month', columns='city', values='temperature')
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
