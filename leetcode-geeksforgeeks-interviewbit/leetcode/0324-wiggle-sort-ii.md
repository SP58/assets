---
title: 0324 wiggle sort ii
tags: leetcode
categories: leetcode
keywords: LeetCode, leetcode solution in Python3 C++ Java, 0324-wiggle-sort-ii solution
description: 0324 wiggle sort ii LeetCode Solution Explained
cover: /assets/img/leetcode-cover-img.webp
---


<h2><a href="https://leetcode.com/problems/wiggle-sort-ii/">324. Wiggle Sort II</a></h2><h3>Medium</h3><hr><div><p>Given an integer array <code>nums</code>, reorder it such that <code>nums[0] &lt; nums[1] &gt; nums[2] &lt; nums[3]...</code>.</p>

<p>You may assume the input array always has a valid answer.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,5,1,1,6,4]
<strong>Output:</strong> [1,6,1,5,1,4]
<strong>Explanation:</strong> [1,4,1,5,1,6] is also accepted.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,3,2,2,3,1]
<strong>Output:</strong> [2,3,1,3,1,2]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 5000</code></li>
	<li>It is guaranteed that there will be an answer for the given input <code>nums</code>.</li>
</ul>

<p>&nbsp;</p>
<strong>Follow Up:</strong> Can you do it in <code>O(n)</code> time and/or <strong>in-place</strong> with <code>O(1)</code> extra space?</div>

---




```python
# https://leetcode.com/problems/wiggle-sort-ii/

class Solution:
    def wiggleSort(self, nums):
        arr = sorted(nums)
        
        # Putting largest element into odd index
        for i in range(1, len(nums), 2):
            nums[i] = arr.pop()
            
        # Putting remaining element into even index
        for i in range(0, len(nums), 2):
            nums[i] = arr.pop()
        
        return nums
```