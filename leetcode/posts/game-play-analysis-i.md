---
title: Game Play Analysis I
summary: Game Play Analysis I - Solution Explained
url: "/posts/game-play-analysis-i"
date: 2020-11-03T17:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Game Play Analysis I LeetCode Solution Explained in all languages", "511", "leetcode question 511", "Game Play Analysis I", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/game-play-analysis-i.webp
    alt: Game Play Analysis I - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [511. Game Play Analysis I](https://leetcode.com/problems/game-play-analysis-i)


## Description

<p>Table: <code>Activity</code></p>

<pre>
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| player_id    | int     |
| device_id    | int     |
| event_date   | date    |
| games_played | int     |
+--------------+---------+
(player_id, event_date) is the primary key (combination of columns with unique values) of this table.
This table shows the activity of players of some games.
Each row is a record of a player who logged in and played a number of games (possibly 0) before logging out on someday using some device.
</pre>

<p>&nbsp;</p>

<p>Write a solution to find the <strong>first login date</strong> for each player.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Activity table:
+-----------+-----------+------------+--------------+
| player_id | device_id | event_date | games_played |
+-----------+-----------+------------+--------------+
| 1         | 2         | 2016-03-01 | 5            |
| 1         | 2         | 2016-05-02 | 6            |
| 2         | 3         | 2017-06-25 | 1            |
| 3         | 1         | 2016-03-02 | 0            |
| 3         | 4         | 2018-07-03 | 5            |
+-----------+-----------+------------+--------------+
<strong>Output:</strong> 
+-----------+-------------+
| player_id | first_login |
+-----------+-------------+
| 1         | 2016-03-01  |
| 2         | 2017-06-25  |
| 3         | 2016-03-02  |
+-----------+-------------+
</pre>

## Solutions

### Solution 1: Group By + Min Function

We can use `GROUP BY` to group the `player_id` and then take the minimum `event_date` in each group as the date when the player first logged into the platform.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
import pandas as pd


def game_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    return (
        activity.groupby("player_id")
        .agg(first_login=("event_date", "min"))
        .reset_index()
    )
```
{{< /terminal >}}

{{< terminal title="SQL Code" >}}
```sql
# Write your MySQL query statement below
SELECT player_id, MIN(event_date) AS first_login
FROM Activity
GROUP BY 1;
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
