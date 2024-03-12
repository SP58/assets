---
title: The Number of Rich Customers
summary: The Number of Rich Customers - Solution Explained
url: "/posts/the-number-of-rich-customers"
date: 2020-08-30T06:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["The Number of Rich Customers LeetCode Solution Explained in all languages", "2082", "leetcode question 2082", "The Number of Rich Customers", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/the-number-of-rich-customers.webp
    alt: The Number of Rich Customers - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2082. The Number of Rich Customers](https://leetcode.com/problems/the-number-of-rich-customers)


## Description

<p>Table: <code>Store</code></p>

<pre>
+-------------+------+
| Column Name | Type |
+-------------+------+
| bill_id     | int  |
| customer_id | int  |
| amount      | int  |
+-------------+------+
bill_id is the primary key (column with unique values) for this table.
Each row contains information about the amount of one bill and the customer associated with it.
</pre>

<p>&nbsp;</p>

<p>Write a solution to report the number of customers who had <strong>at least one</strong> bill with an amount <strong>strictly greater</strong> than <code>500</code>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Store table:
+---------+-------------+--------+
| bill_id | customer_id | amount |
+---------+-------------+--------+
| 6       | 1           | 549    |
| 8       | 1           | 834    |
| 4       | 2           | 394    |
| 11      | 3           | 657    |
| 13      | 3           | 257    |
+---------+-------------+--------+
<strong>Output:</strong> 
+------------+
| rich_count |
+------------+
| 2          |
+------------+
<strong>Explanation:</strong> 
Customer 1 has two bills with amounts strictly greater than 500.
Customer 2 does not have any bills with an amount strictly greater than 500.
Customer 3 has one bill with an amount strictly greater than 500.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT
    COUNT(DISTINCT customer_id) AS rich_count
FROM Store
WHERE amount > 500;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
