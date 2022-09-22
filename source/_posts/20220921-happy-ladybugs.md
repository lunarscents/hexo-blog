---
title: Happy Ladybugs
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
date: 2022-09-21 01:10:00
---

Happy Ladybugs is a board game having the following properties:

- The board is represented by a string, **b**, of length **n**. The **i<sup>th</sup>** character of the string, **b[i]**, denotes the **i<sup>th</sup>** cell of the board.
  - If **b[i]** is an underscore (i.e., \_), it means the **i<sup>th</sup>** cell of the board is empty.
  - If **b[i]** is an uppercase English alphabetic letter (ascii[A-Z]), it means the **i<sup>th</sup>** cell contains a ladybug of color **b[i]**.
  - String **b** will not contain any other characters.
- A ladybug is happy only when its left or right adjacent cell (i.e., **![](https://latex.codecogs.com/svg.image?b[i&space;\pm&space;&space;1])**) is occupied by another ladybug having the same color.
  In a single move, you can move a ladybug from its current position to any empty cell.
  Given the values of and for games of Happy Ladybugs, determine if it's possible to make all the ladybugs happy. For each game, return `YES` if all the ladybugs can be made happy through some number of moves. Otherwise, return `NO`.

<!-- more -->

## Example

**b=[YYR_B_BR]**

You can move the rightmost **B** and **R** to make **b=[YYRRBB__BR__]** and all the ladybugs are happy. Return `YES`.

## Function Description

Complete the happyLadybugs function in the editor below.

happyLadybugs has the following parameters:

- string b: the initial positions and colors of the ladybugs

## Returns

- string: either `YES` or `NO`

## Input Format

The first line contains an integer **g**, the number of games.

The next **g** pairs of lines are in the following format:

The first line contains an integer **n**, the number of cells on the board.
The second line contains a string **b** that describes the **n** cells of the board.

## Constraints

- **1 <= g,n <= 100**
- **![](https://latex.codecogs.com/svg.image?b[i]&space;\in&space;{_,ascii[A&space;-&space;Z]&space;})**

## Sample Input 0

```
4
7
RBY_YBR
6
X_Y__X
2
__
6
B_RRBR
```

## Sample Output 0

```
YES
NO
YES
YES
```

## Explanation 0

The four games of Happy Ladybugs are explained below:

1. Initial board:
   ![](https://s3.amazonaws.com/hr-challenge-images/21763/1474897921-a3088b360d-lady.png)

   After the first move:
   ![](https://s3.amazonaws.com/hr-challenge-images/21763/1474897973-d5796f2e22-lady1.png)

   After the second move:
   ![](https://s3.amazonaws.com/hr-challenge-images/21763/1474898037-7fb2f25594-lady2.png)

   After the third move:
   ![](https://s3.amazonaws.com/hr-challenge-images/21763/1474898044-9df051fcde-lady3.png)

   Now all the ladybugs are happy, so we print `YES` on a new line.

2. There is no way to make the ladybug having color Y happy, so we print NO on a new line.
3. There are no unhappy ladybugs, so we print YES on a new line.
4. Move the rightmost **B** and **R** to form **b=[BBRRR__]**.

## Sample Input 1

```
5
5
AABBC
7
AABBC_C
1
_
10
DD__FQ_QQF
6
AABCBC
```

## Sample Output 1

```
NO
YES
YES
YES
NO
```

---

## Solution

```javascript
/*
 * Complete the 'happyLadybugs' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING b as parameter.
 */

function happyLadybugs(b) {
  // Write your code here
  let result = {};
  let isUnderscore = false;

  for (let i = 0; i < b.length; i++) {
    if (b[i] === '_') {
      isUnderscore = true;
      continue;
    }

    if (!result[b[i]]) {
      result[b[i]] = 0;
    }

    result[b[i]]++;
  }

  if (!isUnderscore) {
    for (let i = 1; i < b.length - 1; i++) {
      if (b[i - 1] !== b[i] && b[i] !== b[i + 1]) {
        return 'NO';
      }
    }
  }

  for (const [key, value] of Object.entries(result)) {
    if (value === 1) return 'NO';
  }

  return 'YES';
}
```
