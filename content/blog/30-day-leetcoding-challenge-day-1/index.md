---
title: "30-Day LeetCoding Challenge #Day1"
date: "2020-04-01T21:26:32.169Z"
description: "I have taken 30-Day LeetCoding Challenge. In this blog we'll discuss day 1's challenge."
---

Given a <b>non-empty</b> array of integers, every element appears twice except for one. Find that single one.

<b>Note:</b>

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

<b>Example 1:</b>
```
Input: [2,2,1]
Output: 1
```

<b>Example 2:</b>
```
Input: [4,1,2,1,2]
Output: 4
```

Give it a try.


If you really wanna see the solution scroll down.

### Solution
We need to solve this in linear time so the first data structure that comes to my mind is hash set which gives linear time lookup.

We'll use the set to store to keep track of the item visited, if we'll find the item again then we'll remove as it is appearing second time.

Eventually our set will contain the answer only.

`gist:karankiri/39fe1d1cf9177b070ef4aa3b2b198090#Leet30DaysChallenge1.py`


Thank you