---
title: Employees Earning More Than Their Managers
summary: Employees Earning More Than Their Managers - Solution Explained
url: "/posts/employees-earning-more-than-their-managers"
date: 2020-11-17T11:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Employees Earning More Than Their Managers LeetCode Solution Explained in all languages", "181", "leetcode question 181", "Employees Earning More Than Their Managers", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/employees-earning-more-than-their-managers.webp
    alt: Employees Earning More Than Their Managers - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [181. Employees Earning More Than Their Managers](https://leetcode.com/problems/employees-earning-more-than-their-managers)


## Description

<p>Table: <code>Employee</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| salary      | int     |
| managerId   | int     |
+-------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table indicates the ID of an employee, their name, salary, and the ID of their manager.
</pre>

<p>&nbsp;</p>

<p>Write a solution&nbsp;to find the employees who earn more than their managers.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Employee table:
+----+-------+--------+-----------+
| id | name  | salary | managerId |
+----+-------+--------+-----------+
| 1  | Joe   | 70000  | 3         |
| 2  | Henry | 80000  | 4         |
| 3  | Sam   | 60000  | Null      |
| 4  | Max   | 90000  | Null      |
+----+-------+--------+-----------+
<strong>Output:</strong> 
+----------+
| Employee |
+----------+
| Joe      |
+----------+
<strong>Explanation:</strong> Joe is the only employee who earns more than his manager.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
import pandas as pd


def find_employees(employee: pd.DataFrame) -> pd.DataFrame:
    df = employee.merge(right=employee, how="left", left_on="managerId", right_on="id")
    emp = df[df["salary_x"] > df["salary_y"]]["name_x"]

    return pd.DataFrame({"Employee": emp})
```
{{< /terminal >}}

{{< terminal title="SQL Code" >}}
```sql
SELECT Name AS Employee
FROM Employee AS Curr
WHERE
    Salary > (
        SELECT Salary
        FROM Employee
        WHERE Id = Curr.ManagerId
    );
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT
    e1.name AS Employee
FROM
    Employee AS e1
    JOIN Employee AS e2 ON e1.managerId = e2.id
WHERE e1.salary > e2.salary;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
