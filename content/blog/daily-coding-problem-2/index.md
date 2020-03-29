---
title: "Daily Coding Problem: Problem #2 [Hard]"
date: "2020-03-30T00:26:32.169Z"
description: "This blog is part of the daily coding problem where I will be sharing solution of one problem in python everday."
---

This problem was asked by Uber.

Given an array of integers, return a new array such that each element at index i of the new array is the product of all the numbers in the original array except the one at i.

For example, if our input was ```[1, 2, 3, 4, 5]```, the expected output would be ```[120, 60, 40, 30, 24]```. If our input was ```[3, 2, 1]```, the expected output would be ```[2, 3, 6]```.

Follow-up: what if you can't use division?

### Solution 1

We can iterate over the list in the loop and calculate the multiplication for every element.
However time complexity for the solution will be O(n<sup>2</sup>).
`gist:karankiri/2684cb0054b12c78429d0acf1e3dd489#DCPSolution2.py`

### Solution 2 

We can use the divison formula to get the multiplication for every element in one pass. Here is what we can do.
```
def ArrayMultiplication(list):
  multiplication = 1
  for item in list:
    multiplication = item * multiplication
  for i in range(len(list)):
    list[i] = multiplication / list[i]
  return list
```
You may think this is the correct answer but it isn't. This code will throw runtime error when there will be atleast one zero in the list. (You know the dreaded divide by zero error &#128542 ).

So think about the edge cases.

Here are the three test cases.
1. List without zero
2. List with one zero
3. List with more than one zero

For case one we can use the above algorithm and for case 3 resultant list will have all zero. (think about it)

For test case 2, all resultant elements will be zero except the i<sup>th</sup>(i is index of zero)

The i<sup>th</sup> index will have mulitplication of all other elements.

We can write the solution as follows.


`gist:karankiri/0bb76cce75637b7b6272e110ec9a1c7f#DCPSolution2Optimized.py`

### Github repository

Here is the github repository [link](https://github.com/karankiri/DailyCodingProblem)

Thank you