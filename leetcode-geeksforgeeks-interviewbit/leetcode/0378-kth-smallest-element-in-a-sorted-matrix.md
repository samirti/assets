---
title: 0378 kth smallest element in a sorted matrix
tags: leetcode
categories: leetcode
keywords: LeetCode, leetcode solution in Python3 C++ Java, 0378-kth-smallest-element-in-a-sorted-matrix solution
description: 0378 kth smallest element in a sorted matrix LeetCode Solution Explained
cover: /assets/img/leetcode-cover-img.webp
---


<h2><a href="https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/">378. Kth Smallest Element in a Sorted Matrix</a></h2><h3>Medium</h3><hr><div><p>Given an <code>n x n</code> <code>matrix</code> where each of the rows and columns is sorted in ascending order, return <em>the</em> <code>k<sup>th</sup></code> <em>smallest element in the matrix</em>.</p>

<p>Note that it is the <code>k<sup>th</sup></code> smallest element <strong>in the sorted order</strong>, not the <code>k<sup>th</sup></code> <strong>distinct</strong> element.</p>

<p>You must find a solution with a memory complexity better than <code>O(n<sup>2</sup>)</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> matrix = [[1,5,9],[10,11,13],[12,13,15]], k = 8
<strong>Output:</strong> 13
<strong>Explanation:</strong> The elements in the matrix are [1,5,9,10,11,12,13,<u><strong>13</strong></u>,15], and the 8<sup>th</sup> smallest number is 13
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> matrix = [[-5]], k = 1
<strong>Output:</strong> -5
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == matrix.length == matrix[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 300</code></li>
	<li><code>-10<sup>9</sup> &lt;= matrix[i][j] &lt;= 10<sup>9</sup></code></li>
	<li>All the rows and columns of <code>matrix</code> are <strong>guaranteed</strong> to be sorted in <strong>non-decreasing order</strong>.</li>
	<li><code>1 &lt;= k &lt;= n<sup>2</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>Could you solve the problem with a constant memory (i.e., <code>O(1)</code> memory complexity)?</li>
	<li>Could you solve the problem in <code>O(n)</code> time complexity? The solution may be too advanced for an interview but you may find reading <a href="http://www.cse.yorku.ca/~andy/pubs/X+Y.pdf" target="_blank">this paper</a> fun.</li>
</ul>
</div>

---




```python
class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
        row = len(matrix); col = len(matrix[0])
        def check(num):
            n = 1
            for i in range(row):
                l, r = 0, col-1
                while l <= r:
                    m = l + (r-l)//2
                    if matrix[i][m] < num:
                        l = m + 1
                    else:
                        r = m - 1
                n += l
            return n <= k
        
        res = matrix[0][0]
        l,r = matrix[0][0], max(matrix[i][-1] for i in range(row))
        while l <= r:
            m = l + (r-l)//2
            if check(m):
                l = m+1
                res = m
            else:
                r = m-1
        return res
```