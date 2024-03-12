---
title: Convert Object to JSON String
summary: Convert Object to JSON String - Solution Explained
url: "/posts/convert-object-to-json-string"
date: 2020-08-07T07:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Convert Object to JSON String LeetCode Solution Explained in all languages", "2633", "leetcode question 2633", "Convert Object to JSON String", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/convert-object-to-json-string.webp
    alt: Convert Object to JSON String - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2633. Convert Object to JSON String](https://leetcode.com/problems/convert-object-to-json-string)


## Description

<p>Given a value, return a valid JSON string of that value. The value can be a string, number, array, object, boolean, or null.&nbsp;The returned string should not include extra spaces. The order of keys should be the same as the order returned by&nbsp;<code>Object.keys()</code>.</p>

<p>Please solve it without using the built-in <code>JSON.stringify</code> method.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> object = {&quot;y&quot;:1,&quot;x&quot;:2}
<strong>Output:</strong> {&quot;y&quot;:1,&quot;x&quot;:2}
<strong>Explanation:</strong> 
Return the JSON representation.
Note that the order of keys should be the same as the order returned by Object.keys().</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> object = {&quot;a&quot;:&quot;str&quot;,&quot;b&quot;:-12,&quot;c&quot;:true,&quot;d&quot;:null}
<strong>Output:</strong> {&quot;a&quot;:&quot;str&quot;,&quot;b&quot;:-12,&quot;c&quot;:true,&quot;d&quot;:null}
<strong>Explanation:</strong>
The primitives of JSON are strings, numbers, booleans, and null.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> object = {&quot;key&quot;:{&quot;a&quot;:1,&quot;b&quot;:[{},null,&quot;Hello&quot;]}}
<strong>Output:</strong> {&quot;key&quot;:{&quot;a&quot;:1,&quot;b&quot;:[{},null,&quot;Hello&quot;]}}
<strong>Explanation:</strong>
Objects and arrays can include other objects and arrays.
</pre>

<p><strong class="example">Example 4:</strong></p>

<pre>
<strong>Input:</strong> object = true
<strong>Output:</strong> true
<strong>Explanation:</strong>
Primitive types are valid inputs.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>value</code> is a valid JSON value</li>
	<li><code>1 &lt;= JSON.stringify(object).length &lt;= 10<sup>5</sup></code></li>
	<li><code>maxNestingLevel &lt;= 1000</code></li>
	<li>all strings contain only alphanumeric characters</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

{{< terminal title="TypeScript Code" >}}
```ts
function jsonStringify(object: any): string {
    if (object === null) {
        return 'null';
    }
    if (typeof object === 'string') {
        return `"${object}"`;
    }
    if (typeof object === 'number' || typeof object === 'boolean') {
        return object.toString();
    }
    if (Array.isArray(object)) {
        return `[${object.map(jsonStringify).join(',')}]`;
    }
    if (typeof object === 'object') {
        return `{${Object.entries(object)
            .map(([key, value]) => `${jsonStringify(key)}:${jsonStringify(value)}`)
            .join(',')}}`;
    }
    return '';
}
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
