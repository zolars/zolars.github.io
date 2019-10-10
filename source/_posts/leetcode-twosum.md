---
title: LeetCode - Two Sum
date: 2017-07-28 15:57:32
categories: Study
tags:
- leetcode
mathjax: true
---

> Do some problems for this summer holiday with python2.7. Learning python3 before but I have to use python2.7 due to the widespread usage (actually because of LeetCode which just provide python2.7). Most code was saved at [zolars/LeetCode-Solution](https://github.com/zolars/LeetCode-Solution), some essays were saved at Blog. So, come on and get to work.

## Problem

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.
You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

<!--more-->

-   Example:
    Given nums = [2, 7, 11, 15], target = 9,
    Because nums[0] + nums[1] = 2 + 7 = 9,
    return [0, 1].

<!--more-->

## Solution

### Brute Force

Because the topic says that each input has one and only one solution, the simplest idea is to compare each pair of values one by one.
The time complexity of this method is $O(n)$

```python
k = 0
for i in nums:
    k += 1
    if target - i in nums[k:]:
        return(k - 1, nums[k:].index(target - i) + k)
```

### Hash Table

Using the brilliant features of Python: The dictionary in Python comes with a hash table and the index speed is very fast. The complexity of searching in the dictionary is $O(1)$, and the complexity in the list is $O(n)$.
Creating a One-pass Hash Table for side-by-side lookups is a good optimization.

```python
lookup = {}
for i, num in enumerate(nums):
    if target - num in lookup:
        return([lookup[target - num], i])
        break
    lookup[num] = i
return([])
```

## Code

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        Method_one : Brute Force
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """

        lookup = {}
        for i, num in enumerate(nums):
            if target - num in lookup:
                return([lookup[target - num], i])
                break
            lookup[num] = i
        return([])

    def twoSum2(self, nums, target):
        """
        Method_two : Hash Table
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """

        k = 0
        for i in nums:
            k += 1
            if target - i in nums[k:]:
                return(k - 1, nums[k:].index(target - i) + k)


if __name__ == '__main__':
    print Solution().twoSum([1, 2, 3, 4], 6)
```
