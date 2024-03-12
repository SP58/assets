---
title: The Number of Employees Which Report to Each Employee
summary: The Number of Employees Which Report to Each Employee - Solution Explained
url: "/posts/the-number-of-employees-which-report-to-each-employee"
date: 2020-09-13T21:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["The Number of Employees Which Report to Each Employee LeetCode Solution Explained in all languages", "1731", "leetcode question 1731", "The Number of Employees Which Report to Each Employee", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/the-number-of-employees-which-report-to-each-employee.webp
    alt: The Number of Employees Which Report to Each Employee - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1731. The Number of Employees Which Report to Each Employee](https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee)


## Description

<p>Table: <code>Employees</code></p>

<pre>
+-------------+----------+
| Column Name | Type     |
+-------------+----------+
| employee_id | int      |
| name        | varchar  |
| reports_to  | int      |
| age         | int      |
+-------------+----------+
employee_id is the column with unique values for this table.
This table contains information about the employees and the id of the manager they report to. Some employees do not report to anyone (reports_to is null). 
</pre>

<p>&nbsp;</p>

<p>For this problem, we will consider a <strong>manager</strong> an employee who has at least 1 other employee reporting to them.</p>

<p>Write a solution to report the ids and the names of all <strong>managers</strong>, the number of employees who report <strong>directly</strong> to them, and the average age of the reports rounded to the nearest integer.</p>

<p>Return the result table ordered by <code>employee_id</code>.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Employees table:
+-------------+---------+------------+-----+
| employee_id | name    | reports_to | age |
+-------------+---------+------------+-----+
| 9           | Hercy   | null       | 43  |
| 6           | Alice   | 9          | 41  |
| 4           | Bob     | 9          | 36  |
| 2           | Winston | null       | 37  |
+-------------+---------+------------+-----+
<strong>Output:</strong> 
+-------------+-------+---------------+-------------+
| employee_id | name  | reports_count | average_age |
+-------------+-------+---------------+-------------+
| 9           | Hercy | 2             | 39          |
+-------------+-------+---------------+-------------+
<strong>Explanation:</strong> Hercy has 2 people report directly to him, Alice and Bob. Their average age is (41+36)/2 = 38.5, which is 39 after rounding it to the nearest integer.
</pre>

## Solutions

### Solution 1: Self-Join + Grouping

We can use self-join to connect the information of each employee's superior manager to the information of each employee, and then use grouping and aggregation to count the number of subordinates and the average age of each manager.

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT
    e2.employee_id,
    e2.name,
    COUNT(1) AS reports_count,
    ROUND(AVG(e1.age)) AS average_age
FROM
    Employees AS e1
    JOIN Employees AS e2 ON e1.reports_to = e2.employee_id
GROUP BY 1
ORDER BY 1;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
