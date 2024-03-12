---
title: Find Customers With Positive Revenue this Year
summary: Find Customers With Positive Revenue this Year - Solution Explained
url: "/posts/find-customers-with-positive-revenue-this-year"
date: 2020-09-10T03:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Find Customers With Positive Revenue this Year LeetCode Solution Explained in all languages", "1821", "leetcode question 1821", "Find Customers With Positive Revenue this Year", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/find-customers-with-positive-revenue-this-year.webp
    alt: Find Customers With Positive Revenue this Year - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1821. Find Customers With Positive Revenue this Year](https://leetcode.com/problems/find-customers-with-positive-revenue-this-year)


## Description

<p>Table: <code>Customers</code></p>

<pre>
+--------------+------+
| Column Name  | Type |
+--------------+------+
| customer_id  | int  |
| year         | int  |
| revenue      | int  |
+--------------+------+
(customer_id, year) is the primary key (combination of columns with unique values) for this table.
This table contains the customer ID and the revenue of customers in different years.
Note that this revenue can be negative.
</pre>

<p>&nbsp;</p>

<p>Write a solution to report the customers with <strong>postive revenue</strong> in the year 2021.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Customers table:
+-------------+------+---------+
| customer_id | year | revenue |
+-------------+------+---------+
| 1           | 2018 | 50      |
| 1           | 2021 | 30      |
| 1           | 2020 | 70      |
| 2           | 2021 | -50     |
| 3           | 2018 | 10      |
| 3           | 2016 | 50      |
| 4           | 2021 | 20      |
+-------------+------+---------+
<strong>Output:</strong> 
+-------------+
| customer_id |
+-------------+
| 1           |
| 4           |
+-------------+
<strong>Explanation:</strong> 
Customer 1 has revenue equal to 30 in the year 2021.
Customer 2 has revenue equal to -50 in the year 2021.
Customer 3 has no revenue in the year 2021.
Customer 4 has revenue equal to 20 in the year 2021.
Thus only customers 1 and 4 have positive revenue in the year 2021.
</pre>

## Solutions

### Solution 1: WHERE Clause

We can directly use the `WHERE` clause to filter out the customers whose `year` is `2021` and `revenue` is greater than $0$.

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT
    customer_id
FROM Customers
WHERE year = '2021' AND revenue > 0;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
