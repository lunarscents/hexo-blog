---
title: Absolute Permutation
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
thumbnail: /images/hackerrank.jpeg
date: 2022-09-24 00:01:00
---

We define **P** to be a permutation of the first **n** natural numbers in the range **[1, n]**. Let **pos[i]** denote the value at position **i** in permutation **P** using **1**-based indexing.

**P** is considered to be an absolute permutation if **|pos[i] - i| = k** holds true for every **![](https://latex.codecogs.com/svg.image?i\in&space;\begin{bmatrix}1,&space;n\end{bmatrix})**.

Given **n** and **k**, print the lexicographically smallest absolute permutation **P**. If no absolute permutation exists, print `-1`.

<!-- more -->

## Example

**n = 4**

**k = 2**

Create an array of elements from **1** to **n**, **pos = [1, 2, 3, 4]**. Using based indexing, create a permutation where every **|pos[i] - i| = k**. It can be rearranged to **[3, 4, 1, 2]** so that all of the absolute differences equal **k = 2**:

```
pos[i]  i   |pos[i] - i|
  3     1        2
  4     2        2
  1     3        2
  2     4        2
```

## Function Description

Complete the absolutePermutation function in the editor below.

absolutePermutation has the following parameter(s):

- int n: the upper bound of natural numbers to consider, inclusive
- int k: the absolute difference between each element's value and its index

## Returns

- int[n]: the lexicographically smallest permutation, or **[-1]** if there is none

## Input Format

The first line contains an integer **t**, the number of queries.
Each of the next **t** lines contains **2** space-separated integers, **n** and **k**.

## Constraints

- **1 <= t <= 10**
- **1 <= n <= 10<sup>5</sup>**
- **1 <= k < k**

## Sample Input

```
STDIN   Function
-----   --------
3       t = 3 (number of queries)
2 1     n = 2, k = 1
3 0     n = 3, k = 0
3 2     n = 3, k = 2
```

## Sample Output

```
2 1
1 2 3
-1
```

## Explanation

Test Case 0:

![](https://s3.amazonaws.com/hr-challenge-images/16007/1462506998-dfe183c6f5-perm.png)

Test Case 1:

![](https://s3.amazonaws.com/hr-challenge-images/16007/1462507102-236cbbd84c-perm1.png)

Test Case 2:

No absolute permutation exists, so we print `-1` on a new line.

---

## Solution

```javascript
/*
 * Complete the 'absolutePermutation' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. INTEGER k
 */

function absolutePermutation(n, k) {
  // Write your code here
  let result = [],
    contain = {},
    x,
    y;

  for (let i = 1; i <= n; i++) {
    x = i - k;
    y = i + k;

    switch (true) {
      case x > 0 && x <= n && !contain[x]:
        result.push(x);
        contain[x] = x;
        break;

      case y > 0 && y <= n && !contain[y]:
        result.push(y);
        contain[y] = y;
        break;

      default:
        return [-1];
    }
  }

  return result;
}
```
