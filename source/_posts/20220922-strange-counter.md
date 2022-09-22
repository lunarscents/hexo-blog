---
title: Strange Counter
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
date: 2022-09-22 00:01:00
---


There is a strange counter. At the first second, it displays the number **3**. Each second, the number displayed by decrements by **1** until it reaches **1**. In next second, the timer resets to **2 X the initial number for the prior cycle** and continues counting down. The diagram below shows the counter values for each time **t** in the first three cycles:

![](https://s3.amazonaws.com/hr-challenge-images/22185/1469447349-bae87a5071-strange1.png)

Find and print the value displayed by the counter at time **t**.

<!-- more -->

## Function Description

Complete the strangeCounter function in the editor below.

strangeCounter has the following parameter(s):

- int t: an integer

## Returns

- int: the value displayed at time **t**

## Input Format

A single integer, the value of **t**.

## Constraints

- **1 <= t <= 10<sup>12</sup>**

## Subtask

- **1 <= t <= 10<sup>5</sup>** for **60%** of the maximum score.

## Sample Input

```
4
```

## Sample Output

```
6
```

## Explanation

Time **t = 4** marks the beginning of the second cycle. It is double the number displayed at the beginning of the first cycle: **![](https://latex.codecogs.com/svg.image?2&space;\times&space;3&space;=&space;6)**. This is shown in the diagram in the problem statement.

---

## Solution

```javascript
/*
 * Complete the 'strangeCounter' function below.
 *
 * The function is expected to return a LONG_INTEGER.
 * The function accepts LONG_INTEGER t as parameter.
 */

function strangeCounter(t) {
  // Write your code here

  let time = 3;

  while (2 * time - 2 <= t) {
    time *= 2;
  }

  return time - (t - (time - 2));
}
```
