---
title: The Grid Search
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
date: 2022-09-20 08:00:00
---


Given an array of strings of digits, try to find the occurrence of a given pattern of digits. In the grid and pattern arrays, each string represents a row in the grid. For example, consider the following grid:

```
1234567890
09**876543**21
11**111111**11
11**111111**11
2222222222
```

The pattern array is:

```
876543
111111
111111
```

The pattern begins at the second row and the third column of the grid and continues in the following two rows. The pattern is said to be present in the grid. The return value should be `YES` or `NO`, depending on whether the pattern is found. In this case, return `YES`.

<!-- more -->

## Function Description

Complete the gridSearch function in the editor below. It should return `YES` if the pattern exists in the grid, or `NO` otherwise.

gridSearch has the following parameter(s):

- string G[R]: the grid to search
- string P[r]: the pattern to search for

## Input Format

The first line contains an integer `t`, the number of test cases.

Each of the `t` test cases is represented as follows:
The first line contains two space-separated integers `R` and `C`, the number of rows in the search grid `G` and the length of each row string.
This is followed by `R` lines, each with a string of `C` digits that represent the grid `G`.
The following line contains two space-separated integers, `r` and `c`, the number of rows in the pattern grid `P` and the length of each pattern row string.
This is followed by `r` lines, each with a string of `c` digits that represent the pattern grid `P`.

## Returns

- string: either `YES` or `NO`

## Constraints

- 1 <= t <= 5
- 1 <= R, r, C, c <= 1000
- 0 <= r <= R
- 0 <= c <= C

## Sample Input

```
2
10 10
7283455864
6731158619
8988242643
3830589324
2229505813
5633845374
6473530293
7053106601
0834282956
4607924137
3 4
9505
3845
3530
15 15
400453592126560
114213133098692
474386082879648
522356951189169
887109450487496
252802633388782
502771484966748
075975207693780
511799789562806
404007454272504
549043809916080
962410809534811
445893523733475
768705303214174
650629270887160
2 2
99
99
```

## Sample Output

```
YES
NO
```

## Explanation

The first test in the input file is:

```
10 10
7283455864
6731158619
8988242643
3830589324
2229505813
5633845374
6473530293
7053106601
0834282956
4607924137
3 4
9505
3845
3530
```

The pattern is present in the larger grid as marked in bold below.

```
7283455864
6731158619
8988242643
3830589324
2229505813
5633845374
6473530293
7053106601
0834282956
4607924137
```

The second test in the input file is:

```
15 15
400453592126560
114213133098692
474386082879648
522356951189169
887109450487496
252802633388782
502771484966748
075975207693780
511799789562806
404007454272504
549043809916080
962410809534811
445893523733475
768705303214174
650629270887160
2 2
99
99
```

The search pattern is:

```
99
99
```

This pattern is not found in the larger grid.

---

## Solution

```javascript
/*
 * Complete the 'gridSearch' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts following parameters:
 *  1. STRING_ARRAY G
 *  2. STRING_ARRAY P
 */

function gridSearch(G: string[], P: string[]): string {
  // Write your code here

  for (let i = 0, itotal = G.length - P.length; i <= itotal; i++) {
    let indexes = [];

    for (let k = 0, ktotal = G[i].length - P[0].length; k <= ktotal; k++) {
      if (G[i].slice(k, k + P[0].length) == P[0]) {
        indexes.push(k);
      }
    }

    if (indexes.length > 0) {
      for (const index of indexes) {
        for (let j = i + 1, jtotal = P.length + i; j < jtotal; j++) {
          if (G[j].slice(index, index + P[j - i].length) != P[j - i]) {
            break;
          }
          if (j - i + 1 == P.length) {
            return 'YES';
          }
        }
      }
    }
  }

  return 'NO';
}
```
