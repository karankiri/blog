---
title: "Maximum Subarray. Leetcode#Day3"
date: "2020-04-04T22:03:32.169Z"
description: "Leetcode 30 day coding challenge. Day 3 solution in python."
---

Given an integer array <code class='language-python'>nums</code>, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

**Example:**
```python
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```


Give it a try.


If you really wanna see the solution scroll down.

### Solution 1

We can solve this problem by brute force. We'll find every possible subarray and it's sum.
The runtime for this approach will be O(n<sup>2</sup>).

```python
def maxSubArray(nums):
  maxSum = nums[0]

  for i in range(len(nums)):
    currSum = nums[i]
    for j in range(i+1, len(nums)):
      currSum = currSum + nums[j]
      if(maxSum < currSum):
        maxSum = currSum
  return maxSum
```

### Solution 2
This is the poster boy question of Dynamic programming. In this approach we'll use the Kagane's algorithm.
Please check this awesome [video tutorial](https://www.youtube.com/watch?v=2MmGzdiKR9Y) for Kagane's algorithm.

Basically this problem can be divided in smaller sub problems. Here the sub problem will be to find the maximum **subarray ending** at all indexes and finding the maximum of it.

To find the maximum sub array **ending** at i<sup>th</sup> index. We can take max of following.
1. Extend the trailing subarray and adding i<sup>th</sup> element to it.
2. New subarray consisting of only i<sup>th</sup> element.

So we can find the maximum sub array **ending** at i<sup>th</sup> index as.
```python
maxSubArrSum = max( maxSubArrSum(i-1) + nums[i], nums[i])
```
We'll do this in O(n) time and space.

```python
def maxSubArrayDP(nums):
  maxSubArraySum = [None] * len(nums)
  currMaxSum = nums[0]
  for i in range(1, len(nums)):
    currMaxSum = max(nums[i] + currMaxSum, nums[i])
    maxSubArraySum[i] = currMaxSum
  return max(maxSubArraySum)
```

We can improvise the above solution and save some space. We can solve this in constant space. Instead of saving the maximum sum for every element we can save the maximum of all the elements visited till now.
```python
def maxSubArray(nums):
  maxSum = nums[0]
  currMaxSum = nums[0]
  for i in range(1, len(nums)):
    currMaxSum = max(nums[i] + currMaxSum, nums[i])
    maxSum = max(currMaxSum, maxSum)
  return maxSum
```

####
Thank you