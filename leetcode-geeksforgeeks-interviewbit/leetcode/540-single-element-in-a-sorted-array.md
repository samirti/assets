---
title: 540 single element in a sorted array
tags: leetcode
categories: leetcode
keywords: LeetCode, leetcode solution in Python3 C++ Java, 540-single-element-in-a-sorted-array solution
description: 540 single element in a sorted array LeetCode Solution Explained
cover: /assets/img/leetcode-cover-img.webp
---


<h2><a href="https://leetcode.com/problems/single-element-in-a-sorted-array/">540. Single Element in a Sorted Array</a></h2><h3>Medium</h3><hr><div><p>You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.</p>

<p>Return <em>the single element that appears only once</em>.</p>

<p>Your solution must run in <code>O(log n)</code> time and <code>O(1)</code> space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,1,2,3,3,4,4,8,8]
<strong>Output:</strong> 2
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [3,3,7,7,10,11,11]
<strong>Output:</strong> 10
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def singleNonDuplicate(self, nums: List[int]) -> int:
        if len(nums) == 1: return nums[0]
        r = len(nums)
        l = 0
        
        while l <= r:
            m = (l + r) // 2
            if m == 0 or m == len(nums)-1: return nums[m]
            
            if m % 2 != 0:
                if nums[m-1] != nums[m] != nums[m+1]: 
                    return nums[m]
                elif nums[m-1] != nums[m]:
                    r = m - 1
                else:
                    l = m + 1
            else:
                if nums[m-1] != nums[m] != nums[m+1]:
                    return nums[m]
                elif nums[m] != nums[m+1]:
                    r = m - 1
                else: 
                    l = m + 1
                    
        return nums[m]
```
