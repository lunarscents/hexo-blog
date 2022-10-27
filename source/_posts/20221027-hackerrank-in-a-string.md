---
title: HackerRank in a String!
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
  - String
  - HackerRank in a String of Algorithms hackerrank solution in javascript
  - HackerRank in a String of Algorithms hackerrank solution in typescript
thumbnail: /images/hackerrank.jpeg
date: 2022-10-27 23:18:06
---

We say that a string contains the word hackerrank if a [subsequence](https://en.wikipedia.org/wiki/Subsequence) of its characters spell the word `hackerrank`. Remeber that a subsequence maintains the order of characters selected from a sequence.

More formally, let **p[0], p[1], ... , p[9]** be the respective indices of `h`, `a`, `c`, `k`, `e`, `r`, `r`, `a`, `n`, `k` in string **s**. If **p[0] < p[1] < p[2] < ... < p[9]** is true, then **s** contains `hackerrank`.

For each query, print `YES` on a new line if the string contains `hackerrank`, otherwise, print `NO`.

<!-- more -->

## Example

**s = haacckkerrannkk**

This contains a subsequence of all of the characters in the proper order. Answer `YES`

**s = haacckkerannk**

This is missing the second 'r'. Answer `NO`.

**s = hccaakkerrannkk**

There is no 'c' after the first occurrence of an 'a', so answer `NO`.

## Function Description

Complete the hackerrankInString function in the editor below.

hackerrankInString has the following parameter(s):

- string s: a string

## Returns

- string: `YES` or `NO`

## Input Format

The first line contains an integer **q**, the number of queries.
Each of the next **q** lines contains a single query string **s**.

## Constraints

- **2 <= q <= 10<sup>2</sup>**

- **10 <= length of s <= 10<sup>4</sup>**

## Sample Input 0

```
2
hereiamstackerrank
hackerworld
```

## Sample Output 0

```
YES
NO
```

## Explanation 0

We perform the following **q = 2** queries:

1. s = **h**ere**ia**msta**ckerrank**
   The characters of `hackerrank` are bolded in the string above. Because the string contains all the characters in `hackerrank` in the same exact order as they appear in `hackerrank`, we return `YES`.

2. s = **hacker**wo**r**ld does not contain the last three characters of `hackerrank`, so we return `NO`.

## Sample Input 1

```
2
hhaacckkekraraannk
rhbaasdndfsdskgbfefdbrsdfhuyatrjtcrtyytktjjt
```

## Sample Output 1

```
YES
NO
```

---

## Solution

### Solution 1 with JS

```javascript
/*
 * Complete the 'hackerrankInString' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING s as parameter.
 */

function hackerrankInString(s) {
  // Write your code here
  const value = 'hackerrank';

  const count = (s.split('') || []).reduce((target, item, index) => {
    value[target] === s[index] && target++;

    return target;
  }, 0);

  return count === value.length ? 'YES' : 'NO';
}
```

### Solution 2 with TS

```typescript
/*
 * Complete the 'hackerrankInString' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING s as parameter.
 */

function hackerrankInString(s: string): string {
  // Write your code here
  const value = 'hackerrank';

  const count = (s.split('') || []).reduce(
    (target: number, item: string, index: number): number => {
      value[target] === s[index] && target++;

      return target;
    },
    0
  );

  return count === value.length ? 'YES' : 'NO';
}
```
