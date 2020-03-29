---
title: "Daily Coding Problem: Problem #1 [Easy]"
date: "2020-03-29T20:26:32.169Z"
description: "This blog is part of the daily coding problem where I will be sharing solution of one problem everday."
---

This problem was recently asked by Google.

Given a list of numbers and a number k, return whether any two numbers from the list add up to k.

For example, given [10, 15, 3, 7] and k of 17, return true since 10 + 7 is 17.

Bonus: Can you do this in one pass?

### Solution 1

We can iterate over the list in the loop and check if two element add up to k.
However time complexity for the solution will be O(n<sup>2</sup>)
`gist:karankiri/b12688dc15b4a30e29f27095b0acf71d#Solution1.py`

### Solution 2 

I wanted to do the bonus part. So we can check this condition in one pass. What we'll do is
use the hashset to store the visited elements as lookup time for hashset is constant (O(1)).
We'll check if the substraction of the sum and current item is present in hash if it's present we can say that the sum exist.
`gist:karankiri/0823aa34fc8ae985cfd28c72da646184#DCPSolution1Optimized.py`

### Github repository

Here is the github repository [link](https://github.com/karankiri/DailyCodingProblem)

Thank you