---
title: Product Sales Analysis II
summary: Product Sales Analysis II - Solution Explained
url: "/posts/product-sales-analysis-ii"
date: 2020-10-11T11:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Product Sales Analysis II LeetCode Solution Explained in all languages", "1069", "leetcode question 1069", "Product Sales Analysis II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/product-sales-analysis-ii.webp
    alt: Product Sales Analysis II - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1069. Product Sales Analysis II](https://leetcode.com/problems/product-sales-analysis-ii)


## Description

<p>Table: <code>Sales</code></p>

<pre>
+-------------+-------+
| Column Name | Type  |
+-------------+-------+
| sale_id     | int   |
| product_id  | int   |
| year        | int   |
| quantity    | int   |
| price       | int   |
+-------------+-------+
(sale_id, year) is the primary key (combination of columns with unique values) of this table.
product_id is a foreign key (reference column) to <code>Product</code> table.
Each row of this table shows a sale on the product product_id in a certain year.
Note that the price is per unit.
</pre>

<p>&nbsp;</p>

<p>Table: <code>Product</code></p>

<pre>
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| product_id   | int     |
| product_name | varchar |
+--------------+---------+
product_id is the primary key (column with unique values) of this table.
Each row of this table indicates the product name of each product.
</pre>

<p>&nbsp;</p>

<p>Write a solution that reports the total quantity sold for every product id.</p>

<p>Return the resulting table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Sales table:
+---------+------------+------+----------+-------+
| sale_id | product_id | year | quantity | price |
+---------+------------+------+----------+-------+ 
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |
+---------+------------+------+----------+-------+
Product table:
+------------+--------------+
| product_id | product_name |
+------------+--------------+
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |
+------------+--------------+
<strong>Output:</strong> 
+--------------+----------------+
| product_id   | total_quantity |
+--------------+----------------+
| 100          | 22             |
| 200          | 15             |
+--------------+----------------+
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT product_id, SUM(quantity) AS total_quantity
FROM Sales
GROUP BY 1;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
