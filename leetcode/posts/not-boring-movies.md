---
title: Not Boring Movies
summary: Not Boring Movies - Solution Explained
url: "/posts/not-boring-movies"
date: 2020-10-30T04:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Not Boring Movies LeetCode Solution Explained in all languages", "620", "leetcode question 620", "Not Boring Movies", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/not-boring-movies.webp
    alt: Not Boring Movies - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [620. Not Boring Movies](https://leetcode.com/problems/not-boring-movies)


## Description

<p>Table: <code>Cinema</code></p>

<pre>
+----------------+----------+
| Column Name    | Type     |
+----------------+----------+
| id             | int      |
| movie          | varchar  |
| description    | varchar  |
| rating         | float    |
+----------------+----------+
id is the primary key (column with unique values) for this table.
Each row contains information about the name of a movie, its genre, and its rating.
rating is a 2 decimal places float in the range [0, 10]
</pre>

<p>&nbsp;</p>

<p>Write a solution to report the movies with an odd-numbered ID and a description that is not <code>&quot;boring&quot;</code>.</p>

<p>Return the result table ordered by <code>rating</code> <strong>in descending order</strong>.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Cinema table:
+----+------------+-------------+--------+
| id | movie      | description | rating |
+----+------------+-------------+--------+
| 1  | War        | great 3D    | 8.9    |
| 2  | Science    | fiction     | 8.5    |
| 3  | irish      | boring      | 6.2    |
| 4  | Ice song   | Fantacy     | 8.6    |
| 5  | House card | Interesting | 9.1    |
+----+------------+-------------+--------+
<strong>Output:</strong> 
+----+------------+-------------+--------+
| id | movie      | description | rating |
+----+------------+-------------+--------+
| 5  | House card | Interesting | 9.1    |
| 1  | War        | great 3D    | 8.9    |
+----+------------+-------------+--------+
<strong>Explanation:</strong> 
We have three movies with odd-numbered IDs: 1, 3, and 5. The movie with ID = 3 is boring so we do not include it in the answer.
</pre>

## Solutions

### Solution 1: Conditional Filtering + Sorting

We can use the `WHERE` clause to filter out the records where `description` is not `boring` and `id` is odd, and then use the `ORDER BY` clause to sort the result in descending order by `rating`.

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT *
FROM Cinema
WHERE description != 'boring' AND id & 1 = 1
ORDER BY 4 DESC;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
