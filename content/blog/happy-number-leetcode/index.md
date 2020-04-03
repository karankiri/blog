---
title: "Happy Number. Leetcode#Day2"
date: "2020-04-02T23:26:32.169Z"
description: "Leetcode 30day coding challenge. Day 2 solution in python."
---

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

<b>Example: </b>
<pre class='language-text'>
<code class='language-text'>
Input: 19
Output: true
Explanation: 
1<sup>2</sup> + 9<sup>2</sup> = 82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1
</code>
</pre>
Give it a try.


If you really wanna see the solution scroll down.

### Solution 1

We can solve this proble by brute force. We'll keep computing the square and see where it leads.
After repeting this for few time you'll notice that either we'll reach 1 or we'll keep repeating the cycle.

So we'll use the set to keep track of visited numbers, if we found that number then we can say that we're in infinite loop and we'll return false. If we reach 1 then we're done.

Here's the accepted solution.

```python
class Solution:
    def isHappy(self, n: int) -> bool:
      is_happy = False
      visites_sqares = set()
      currentSq = 0
      while n not in visites_sqares:
        visites_sqares.add(n)
        currentSq = digitSqaures(n)
        if(n==1):
          is_happy = True
          break
        n = currentSq
      return is_happy
     
def digitSqaures(n:int) -> int:
    sum = 0
    while n > 0:
        remainder = n % 10
        sum = sum + remainder * remainder
        n = int(n / 10)
    return sum
```

### Solution 2
In this approach we'll use the Floyd's algorithm for checking if there's any cycle in the list we're following.
If you don't know about Floyd's algorithm, please check this awesome [video tutorial](https://www.youtube.com/watch?v=-YiQZi3mLq0) by Gaurav Sen.

Basically we'll follow two pointer one fast and slow. If both reached the same node then we can say that there's cycle and we can return false. If we reach 1 then we'll return true.

Here is the solution.

```python
class Solution:
    def isHappy(self, n: int) -> bool:
      is_happy = n == 1
      fastSq = digitSqaures(n)

      while n!= 1 and fastSq != n:
        n = digitSqaures(n)
        fastSq = digitSqaures(digitSqaures(fastSq))
        if(n==1):
          is_happy = True
          break
      return is_happy
               
def digitSqaures(n:int) -> int:
    sum = 0
    while n > 0:
        remainder = n % 10
        sum = sum + remainder * remainder
        n = int(n / 10)
    return sum
```

####
Thank you