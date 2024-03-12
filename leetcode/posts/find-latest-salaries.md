---
title: Find Latest Salaries
summary: Find Latest Salaries - Solution Explained
url: "/posts/find-latest-salaries"
date: 2020-08-05T20:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Find Latest Salaries LeetCode Solution Explained in all languages", "2668", "leetcode question 2668", "Find Latest Salaries", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/find-latest-salaries.webp
    alt: Find Latest Salaries - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2668. Find Latest Salaries](https://leetcode.com/problems/find-latest-salaries)


## Description

<p>Table: <code><font face="monospace">Salary</font></code></p>

<pre>
+---------------+---------+ 
| Column Name   | Type    | 
+---------------+---------+ 
| emp_id        | int     | 
| firstname     | varchar |
| lastname      | varchar |
| salary        | varchar |
| department_id | varchar |
+---------------+---------+
(emp_id, salary) is the primary key (combination of columns with unique values) for this table.
Each row contains employees details and their yearly salaries, however, some of the records are old and contain outdated salary information. 
</pre>

<p>Write a solution to find the current salary of each employee assuming that salaries increase each year. Output their <code>emp_id</code>, <code>firstname</code>, <code>lastname</code>, <code>salary</code>, and <code>department_id</code>.</p>

<p>Return the result table ordered&nbsp;by <code>emp_id</code> in <strong>ascending</strong> order<em>.</em></p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:
</strong><code>Salary</code> table:
+--------+-----------+----------+--------+---------------+
| emp_id | firstname | lastname | salary | department_id |
+--------+-----------+----------+--------+---------------+ 
| 1      | Todd      | Wilson   | 110000 | D1006         |
| 1      | Todd      | Wilson   | 106119 | D1006         | 
| 2      | Justin    | Simon    | 128922 | D1005         | 
| 2      | Justin    | Simon    | 130000 | D1005         | 
| 3      | Kelly     | Rosario  | 42689  | D1002         | 
| 4      | Patricia  | Powell   | 162825 | D1004         |
| 4      | Patricia  | Powell   | 170000 | D1004         |
| 5      | Sherry    | Golden   | 44101  | D1002         | 
| 6      | Natasha   | Swanson  | 79632  | D1005         | 
| 6      | Natasha   | Swanson  | 90000  | D1005         |
+--------+-----------+----------+--------+---------------+
<strong>Output:
</strong>+--------+-----------+----------+--------+---------------+
| emp_id | firstname | lastname | salary | department_id |
+--------+-----------+----------+--------+---------------+ 
| 1      | Todd      | Wilson   | 110000 | D1006         |
| 2      | Justin    | Simon    | 130000 | D1005         | 
| 3      | Kelly     | Rosario  | 42689  | D1002         | 
| 4      | Patricia  | Powell   | 170000 | D1004         |
| 5      | Sherry    | Golden   | 44101  | D1002         | 
| 6      | Natasha   | Swanson  | 90000  | D1005         |
+--------+-----------+----------+--------+---------------+<strong>
</strong>
<strong>Explanation:</strong>
- emp_id 1 has two records with a salary of&nbsp;110000, 106119 out of these 110000 is an updated salary (Assuming salary is increasing each year)
- emp_id 2 has two records with a salary of&nbsp;128922, 130000&nbsp;out of these 130000 is an updated salary.
- emp_id 3 has only one salary record so that is already an updated salary.
- emp_id 4&nbsp;has two records with a salary of&nbsp;162825, 170000&nbsp;out of these 170000 is an updated salary.
- emp_id 5&nbsp;has only one salary record so that is already an updated salary.
- emp_id 6&nbsp;has two records with a salary of 79632, 90000 out&nbsp;of these 90000 is an updated salary.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT
    emp_id,
    firstname,
    lastname,
    MAX(salary) AS salary,
    department_id
FROM Salary
GROUP BY emp_id
ORDER BY emp_id;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
