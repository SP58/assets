---
title: 1729 Find Followers Count
summary: 1729 Find Followers Count LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1729 Find Followers Count LeetCode Solution Explained in all languages", "1729 Find Followers Count", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1729 Find Followers Count - Solution Explained/problem-solving.webp
    alt: 1729 Find Followers Count
    hiddenInList: true
    hiddenInSingle: false
---


# [1729. Find Followers Count](https://leetcode.com/problems/find-followers-count)


## Description

<p>Table: <code>Followers</code></p>

<pre>
+-------------+------+
| Column Name | Type |
+-------------+------+
| user_id     | int  |
| follower_id | int  |
+-------------+------+
(user_id, follower_id) is the primary key (combination of columns with unique values) for this table.
This table contains the IDs of a user and a follower in a social media app where the follower follows the user.</pre>

<p>&nbsp;</p>

<p>Write a solution that will, for each user, return the number of followers.</p>

<p>Return the result table ordered by <code>user_id</code> in ascending order.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Followers table:
+---------+-------------+
| user_id | follower_id |
+---------+-------------+
| 0       | 1           |
| 1       | 0           |
| 2       | 0           |
| 2       | 1           |
+---------+-------------+
<strong>Output:</strong> 
+---------+----------------+
| user_id | followers_count|
+---------+----------------+
| 0       | 1              |
| 1       | 1              |
| 2       | 2              |
+---------+----------------+
<strong>Explanation:</strong> 
The followers of 0 are {1}
The followers of 1 are {0}
The followers of 2 are {0,1}
</pre>

## Solutions

### Solution 1: Grouping and Aggregation

We can directly group the `Followers` table by `user_id`, and use the `COUNT` function to count the number of followers for each user.

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT user_id, COUNT(1) AS followers_count
FROM Followers
GROUP BY 1
ORDER BY 1;
```

<!-- tabs:end -->

<!-- end -->
