---
title: Manasa and Stones
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
  - TypeScript
thumbnail: /images/hackerrank.jpeg
date: 2022-09-19 08:30:00
---


Manasa is out on a hike with friends. She finds a trail of stones with numbers on them. She starts following the trail and notices that any two consecutive stones' numbers differ by one of two values. Legend has it that there is a treasure trove at the end of the trail. If Manasa can guess the value of the last stone, the treasure will be hers.

<!-- more -->

## Example

**<p align="center">n = 2</p>**

**<p align="center">a = 2</p>**

**<p align="center">b = 3</p>**

She finds stones and their differences are **a = 2** or **b = 3**. We know she starts with a **0** stone not included in her count. The permutations of differences for the two stones are **[2, 2], [2, 3], [3, 2]** or **[3, 3]**. Looking at each scenario, stones might have **[2, 4], [2, 5], [3, 5]** or **[3, 6]** on them. The last stone might have any of **4**, **5** or **6** on its face.

Compute all possible numbers that might occur on the last stone given a starting stone with a **0** on it, a number of additional stones found, and the possible differences between consecutive stones. Order the list ascending.

## Function Description

Complete the stones function in the editor below.
stones has the following parameter(s):

- int n: the number of non-zero stones
- int a: one possible integer difference
- int b: another possible integer difference

## Returns

- int[]: all possible values of the last stone, sorted ascending

## Input Format

The first line contains an integer , the number of test cases.

Each test case contains lines:

- The first line contains , the number of non-zero stones found.
- The second line contains , one possible difference
- The third line contains , the other possible difference.

## Constraints

- 1 <= T <= 10
- 1 <= n, a, b <= 10<sup>3</sup>

## Sample Input

```
STDIN   Function
-----   --------
2       T = 2 (test cases)
3       n = 3 (test case 1)
1       a = 1
2       b = 2
4       n = 4 (test case 2)
10      a = 10
100     b = 100
```

## Sample Output

```
2 3 4
30 120 210 300
```

## Explanation

With differences 1 and 2, all possible series for the first test case are given below:

1. 0,1,2
2. 0,1,3
3. 0,2,3
4. 0,2,4

Hence the answer `2 3 4`.

With differences 10 and 100, all possible series for the second test case are the following:

1. 0, 10, 20, **30**
2. 0, 10, 20, **120**
3. 0, 10, 110, **120**
4. 0, 10, 110, **210**
5. 0, 100, 110, **120**
6. 0, 100, 110, **210**
7. 0, 100, 200, **210**
8. 0, 100, 200, **300**

Hence the answer `30 120 210 300`.

---

## Solution

### Solution 1 with JS

```javascript
/*
 * Complete the 'stones' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. INTEGER a
 *  3. INTEGER b
 */

function stones(n, a, b) {
  // Write your code here
  return new Array(n)
    .fill(0)
    .map((item, index) => a * (n - index - 1) + b * index)
    .sort((a, b) => a - b)
    .reduce((target, item) => {
      !target.includes(item) && target.push(item);

      return target;
    }, []);
}
```

### Solution 2 with TS

```typescript
/*
 * Complete the 'stones' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. INTEGER a
 *  3. INTEGER b
 */

function stones(n: number, a: number, b: number): number[] {
  // Write your code here
  return new Array(n)
    .fill(0)
    .map((item: number, index: number) => a * (n - index - 1) + b * index)
    .sort((a, b) => a - b)
    .reduce((target: number[], item: number) => {
      // includes 문법은 ES7 (ES2016)부터 지원된다.
      !target.includes(item) && target.push(item);

      return target;
    }, [] as number[]);
}
```
