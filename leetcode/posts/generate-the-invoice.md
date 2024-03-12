---
title: Generate the Invoice
summary: Generate the Invoice - Solution Explained
url: "/posts/generate-the-invoice"
date: 2020-08-18T14:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Generate the Invoice LeetCode Solution Explained in all languages", "2362", "leetcode question 2362", "Generate the Invoice", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/generate-the-invoice.webp
    alt: Generate the Invoice - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2362. Generate the Invoice](https://leetcode.com/problems/generate-the-invoice)


## Description

<p>Table: <code>Products</code></p>

<pre>
+-------------+------+
| Column Name | Type |
+-------------+------+
| product_id  | int  |
| price       | int  |
+-------------+------+
product_id contains unique values.
Each row in this table shows the ID of a product and the price of one unit.
</pre>

<p>&nbsp;</p>

<p>Table: <code>Purchases</code></p>

<pre>
+-------------+------+
| Column Name | Type |
+-------------+------+
| invoice_id  | int  |
| product_id  | int  |
| quantity    | int  |
+-------------+------+
(invoice_id, product_id) is the primary key (combination of columns with unique values) for this table.
Each row in this table shows the quantity ordered from one product in an invoice. 
</pre>

<p>&nbsp;</p>

<p>Write a solution to show the details of the invoice with the highest price. If two or more invoices have the same price, return the details of the one with the smallest <code>invoice_id</code>.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The&nbsp;result format is shown in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Products table:
+------------+-------+
| product_id | price |
+------------+-------+
| 1          | 100   |
| 2          | 200   |
+------------+-------+
Purchases table:
+------------+------------+----------+
| invoice_id | product_id | quantity |
+------------+------------+----------+
| 1          | 1          | 2        |
| 3          | 2          | 1        |
| 2          | 2          | 3        |
| 2          | 1          | 4        |
| 4          | 1          | 10       |
+------------+------------+----------+
<strong>Output:</strong> 
+------------+----------+-------+
| product_id | quantity | price |
+------------+----------+-------+
| 2          | 3        | 600   |
| 1          | 4        | 400   |
+------------+----------+-------+
<strong>Explanation:</strong> 
Invoice 1: price = (2 * 100) = $200
Invoice 2: price = (4 * 100) + (3 * 200) = $1000
Invoice 3: price = (1 * 200) = $200
Invoice 4: price = (10 * 100) = $1000

The highest price is $1000, and the invoices with the highest prices are 2 and 4. We return the details of the one with the smallest ID, which is invoice 2.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
WITH
    P AS (
        SELECT *
        FROM
            Purchases
            JOIN Products USING (product_id)
    ),
    T AS (
        SELECT invoice_id, SUM(price * quantity) AS amount
        FROM P
        GROUP BY invoice_id
        ORDER BY 2 DESC, 1
        LIMIT 1
    )
SELECT product_id, quantity, (quantity * price) AS price
FROM
    P
    JOIN T USING (invoice_id);
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
