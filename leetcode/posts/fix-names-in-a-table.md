---
title: Fix Names in a Table
summary: Fix Names in a Table - Solution Explained
url: "/posts/fix-names-in-a-table"
date: 2020-09-16T13:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Fix Names in a Table LeetCode Solution Explained in all languages", "1667", "leetcode question 1667", "Fix Names in a Table", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/fix-names-in-a-table.webp
    alt: Fix Names in a Table - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1667. Fix Names in a Table](https://leetcode.com/problems/fix-names-in-a-table)


## Description

<p>Table: <code>Users</code></p>

<pre>
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| user_id        | int     |
| name           | varchar |
+----------------+---------+
user_id is the primary key (column with unique values) for this table.
This table contains the ID and the name of the user. The name consists of only lowercase and uppercase characters.
</pre>

<p>&nbsp;</p>

<p>Write a solution to fix the names so that only the first character is uppercase and the rest are lowercase.</p>

<p>Return the result table ordered by <code>user_id</code>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Users table:
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | aLice |
| 2       | bOB   |
+---------+-------+
<strong>Output:</strong> 
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | Alice |
| 2       | Bob   |
+---------+-------+
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
SELECT
    user_id,
    CONCAT(UPPER(LEFT(name, 1)), LOWER(SUBSTRING(name, 2))) AS name
FROM
    users
ORDER BY
    user_id;
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
SELECT
    user_id,
    CONCAT(
        UPPER(LEFT(name, 1)),
        LOWER(SUBSTRING(name, 2, DATALENGTH(name)))
    ) AS name
FROM
    users
ORDER BY
    user_id;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
