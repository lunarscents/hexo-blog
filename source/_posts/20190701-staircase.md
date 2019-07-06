---
title: 'Staircase'
thumbnail: '/images/hackerrank.jpeg'
categories:
  - Algorithm
  - HackerRank
  - Problem Solving
tags:
  - Algorithm
  - HackerRank
  - Problem Solving
  - JavaScript
  - ES6
date: 2019-07-01 12:50:30
---

Consider a staircase of size **n = 4**:

```
   #
  ##
 ###
####
```

<!-- more -->

Observe that its base and height are both equal to **n**, and the image is drawn using # symbols and spaces. The last line is not preceded by any spaces.

Write a program that prints a staircase of size **n**.

## Function Description

Complete the staircase function in the editor below. It should print a staircase as described above.

staircase has the following parameter(s):

- n: an integer

## Input Format

A single integer, **n**, denoting the size of the staircase.

## Constraints 

**0 < n <= 100**

## Output Format

Print a staircase of size **n** using # symbols and spaces.

Note: The last line must have **0** spaces in it.

## Sample Input

```
6
```

## Sample Output

```
     #
    ##
   ###
  ####
 #####
######
```

## Explanation

The staircase is right-aligned, composed of # symbols and spaces, and has a height and width of **n = 6**.

---

## Solution

```javascript
// Complete the staircase function below.
function staircase(n) {
    new Array(n).fill('#'.repeat(n)).reduce((target, item, index) => {

        item = item.replace(/\#/g, (value, itemIndex) => (itemIndex < n - index - 1) ? ' ' : value);

        console.log(item);

        return target;
    }, []);
}
```