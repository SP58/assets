---
title: Find Users With Valid E-Mails
summary: Find Users With Valid E-Mails - Solution Explained
url: "/posts/find-users-with-valid-e-mails"
date: 2020-09-22T19:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Find Users With Valid E-Mails LeetCode Solution Explained in all languages", "1517", "leetcode question 1517", "Find Users With Valid E-Mails", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/find-users-with-valid-e-mails.webp
    alt: Find Users With Valid E-Mails - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1517. Find Users With Valid E-Mails](https://leetcode.com/problems/find-users-with-valid-e-mails)


## Description

<p>Table: <code>Users</code></p>

<pre>
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| user_id       | int     |
| name          | varchar |
| mail          | varchar |
+---------------+---------+
user_id is the primary key (column with unique values) for this table.
This table contains information of the users signed up in a website. Some e-mails are invalid.
</pre>

<p>&nbsp;</p>

<p>Write a solution to find the users who have <strong>valid emails</strong>.</p>

<p>A valid e-mail has a prefix name and a domain where:</p>

<ul>
	<li><strong>The prefix name</strong> is a string that may contain letters (upper or lower case), digits, underscore <code>&#39;_&#39;</code>, period <code>&#39;.&#39;</code>, and/or dash <code>&#39;-&#39;</code>. The prefix name <strong>must</strong> start with a letter.</li>
	<li><strong>The domain</strong> is <code>&#39;@leetcode.com&#39;</code>.</li>
</ul>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Users table:
+---------+-----------+-------------------------+
| user_id | name      | mail                    |
+---------+-----------+-------------------------+
| 1       | Winston   | winston@leetcode.com    |
| 2       | Jonathan  | jonathanisgreat         |
| 3       | Annabelle | bella-@leetcode.com     |
| 4       | Sally     | sally.come@leetcode.com |
| 5       | Marwan    | quarz#2020@leetcode.com |
| 6       | David     | david69@gmail.com       |
| 7       | Shapiro   | .shapo@leetcode.com     |
+---------+-----------+-------------------------+
<strong>Output:</strong> 
+---------+-----------+-------------------------+
| user_id | name      | mail                    |
+---------+-----------+-------------------------+
| 1       | Winston   | winston@leetcode.com    |
| 3       | Annabelle | bella-@leetcode.com     |
| 4       | Sally     | sally.come@leetcode.com |
+---------+-----------+-------------------------+
<strong>Explanation:</strong> 
The mail of user 2 does not have a domain.
The mail of user 5 has the # sign which is not allowed.
The mail of user 6 does not have the leetcode domain.
The mail of user 7 starts with a period.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT *
FROM Users
WHERE mail REGEXP '^[a-zA-Z][a-zA-Z0-9_.-]*@leetcode[.]com$';
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
