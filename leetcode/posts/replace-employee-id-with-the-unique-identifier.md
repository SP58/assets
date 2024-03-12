---
title: Replace Employee ID With The Unique Identifier
summary: Replace Employee ID With The Unique Identifier - Solution Explained
url: "/posts/replace-employee-id-with-the-unique-identifier"
date: 2020-09-28T14:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Replace Employee ID With The Unique Identifier LeetCode Solution Explained in all languages", "1378", "leetcode question 1378", "Replace Employee ID With The Unique Identifier", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/replace-employee-id-with-the-unique-identifier.webp
    alt: Replace Employee ID With The Unique Identifier - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1378. Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier)


## Description

<p>Table: <code>Employees</code></p>

<pre>
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| name          | varchar |
+---------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table contains the id and the name of an employee in a company.
</pre>

<p>&nbsp;</p>

<p>Table: <code>EmployeeUNI</code></p>

<pre>
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| unique_id     | int     |
+---------------+---------+
(id, unique_id) is the primary key (combination of columns with unique values) for this table.
Each row of this table contains the id and the corresponding unique id of an employee in the company.
</pre>

<p>&nbsp;</p>

<p>Write a solution to show the <strong>unique ID </strong>of each user, If a user does not have a unique ID replace just show <code>null</code>.</p>

<p>Return the result table in <strong>any</strong> order.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Employees table:
+----+----------+
| id | name     |
+----+----------+
| 1  | Alice    |
| 7  | Bob      |
| 11 | Meir     |
| 90 | Winston  |
| 3  | Jonathan |
+----+----------+
EmployeeUNI table:
+----+-----------+
| id | unique_id |
+----+-----------+
| 3  | 1         |
| 11 | 2         |
| 90 | 3         |
+----+-----------+
<strong>Output:</strong> 
+-----------+----------+
| unique_id | name     |
+-----------+----------+
| null      | Alice    |
| null      | Bob      |
| 2         | Meir     |
| 3         | Winston  |
| 1         | Jonathan |
+-----------+----------+
<strong>Explanation:</strong> 
Alice and Bob do not have a unique ID, We will show null instead.
The unique ID of Meir is 2.
The unique ID of Winston is 3.
The unique ID of Jonathan is 1.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT unique_id, name
FROM
    Employees
    LEFT JOIN EmployeeUNI USING (id);
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
