---
title: Product Price at a Given Date
summary: Product Price at a Given Date - Solution Explained
url: "/posts/product-price-at-a-given-date"
date: 2020-10-07T12:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Product Price at a Given Date LeetCode Solution Explained in all languages", "1164", "leetcode question 1164", "Product Price at a Given Date", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/product-price-at-a-given-date.webp
    alt: Product Price at a Given Date - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1164. Product Price at a Given Date](https://leetcode.com/problems/product-price-at-a-given-date)


## Description

<p>Table: <code>Products</code></p>

<pre>
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| product_id    | int     |
| new_price     | int     |
| change_date   | date    |
+---------------+---------+
(product_id, change_date) is the primary key (combination of columns with unique values) of this table.
Each row of this table indicates that the price of some product was changed to a new price at some date.</pre>

<p>&nbsp;</p>

<p>Write a solution to find the prices of all products on <code>2019-08-16</code>. Assume the price of all products before any change is <code>10</code>.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Products table:
+------------+-----------+-------------+
| product_id | new_price | change_date |
+------------+-----------+-------------+
| 1          | 20        | 2019-08-14  |
| 2          | 50        | 2019-08-14  |
| 1          | 30        | 2019-08-15  |
| 1          | 35        | 2019-08-16  |
| 2          | 65        | 2019-08-17  |
| 3          | 20        | 2019-08-18  |
+------------+-----------+-------------+
<strong>Output:</strong> 
+------------+-------+
| product_id | price |
+------------+-------+
| 2          | 50    |
| 1          | 35    |
| 3          | 10    |
+------------+-------+
</pre>

## Solutions

### Solution 1: Subquery + Join

We can use a subquery to find the price of the last price change for each product before the given date, and record it in the `P` table. Then, we can find all `product_id`s in the `T` table. Finally, we can left join the `T` table with the `P` table on `product_id` to get the final result.

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
WITH
    T AS (SELECT DISTINCT product_id FROM Products),
    P AS (
        SELECT product_id, new_price AS price
        FROM Products
        WHERE
            (product_id, change_date) IN (
                SELECT product_id, MAX(change_date) AS change_date
                FROM Products
                WHERE change_date <= '2019-08-16'
                GROUP BY 1
            )
    )
SELECT product_id, IFNULL(price, 10) AS price
FROM
    T
    LEFT JOIN P USING (product_id);
```
{{< /terminal >}}

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
WITH
    P AS (
        SELECT p1.product_id, new_price, change_date
        FROM
            (
                SELECT DISTINCT product_id
                FROM Products
            ) AS p1
            LEFT JOIN Products AS p2
                ON p1.product_id = p2.product_id AND p2.change_date <= '2019-08-16'
    ),
    T AS (
        SELECT
            *,
            RANK() OVER (
                PARTITION BY product_id
                ORDER BY change_date DESC
            ) AS rk
        FROM P
    )
SELECT product_id, IFNULL(new_price, 10) AS price
FROM T
WHERE rk = 1;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
