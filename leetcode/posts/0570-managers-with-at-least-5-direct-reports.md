---
title: 0570 Managers with at Least 5 Direct Reports
summary: 0570 Managers with at Least 5 Direct Reports LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0570 Managers with at Least 5 Direct Reports LeetCode Solution Explained in all languages", "0570 Managers with at Least 5 Direct Reports", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0570 Managers with at Least 5 Direct Reports - Solution Explained/problem-solving.webp
    alt: 0570 Managers with at Least 5 Direct Reports
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [570. Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports)


## Description

<p>Table: <code>Employee</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |
+-------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table indicates the name of an employee, their department, and the id of their manager.
If managerId is null, then the employee does not have a manager.
No employee will be the manager of themself.
</pre>

<p>&nbsp;</p>

<p>Write a solution to find managers with at least <strong>five direct reports</strong>.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Employee table:
+-----+-------+------------+-----------+
| id  | name  | department | managerId |
+-----+-------+------------+-----------+
| 101 | John  | A          | null      |
| 102 | Dan   | A          | 101       |
| 103 | James | A          | 101       |
| 104 | Amy   | A          | 101       |
| 105 | Anne  | A          | 101       |
| 106 | Ron   | B          | 101       |
+-----+-------+------------+-----------+
<strong>Output:</strong> 
+------+
| name |
+------+
| John |
+------+
</pre>

## Solutions

### Solution 1: Grouping and Joining

We can first count the number of direct subordinates for each manager, and then join the `Employee` table to find the managers whose number of direct subordinates is greater than or equal to $5$.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
import pandas as pd


def find_managers(employee: pd.DataFrame) -> pd.DataFrame:
    # Group the employees by managerId and count the number of direct reports
    manager_report_count = (
        employee.groupby("managerId").size().reset_index(name="directReports")
    )

    # Filter managers with at least five direct reports
    result = manager_report_count[manager_report_count["directReports"] >= 5]

    # Merge with the Employee table to get the names of these managers
    result = result.merge(
        employee[["id", "name"]], left_on="managerId", right_on="id", how="inner"
    )

    # Select only the 'name' column and drop the 'id' and 'directReports' columns
    result = result[["name"]]

    return result
```
{{< /terminal >}}

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT name
FROM
    Employee
    JOIN (
        SELECT managerId AS id, COUNT(1) AS cnt
        FROM Employee
        GROUP BY 1
        HAVING cnt >= 5
    ) AS t
        USING (id);
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
