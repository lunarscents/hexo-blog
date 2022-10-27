---
title: 3D Surface Area
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
date: 2022-09-23 01:29:00
---


Madison is a little girl who is fond of toys. Her friend Mason works in a toy manufacturing factory. Mason has a 2D board **A** of size **![](https://latex.codecogs.com/svg.image?H&space;\times&space;W)** with **H** rows and **W** columns. The board is divided into cells of size **![](https://latex.codecogs.com/svg.image?1&space;\times&space;1)** with each cell indicated by its coordinate **(i,j)**. The cell **(i,j)** has an integer **A<sub>ij</sub>** written on it. To create the toy Mason stacks **A<sub>ij</sub>** number of cubes of size **![](https://latex.codecogs.com/svg.image?1&space;\times&space;1\times&space;1)** on the cell **(i, j)**.

Given the description of the board showing the values of **A<sub>ij</sub>** and that the price of the toy is equal to the 3d surface area find the price of the toy.

<!-- more -->

## Input Format

The first line contains two space-separated integers **H** and **W** the height and the width of the board respectively.

The next **H** lines contains **W** space separated integers. The **j<sup>th</sup>** integer in **i<sup>th</sup>** line denotes **A<sub>ij</sub>**.

## Constraints

- **1 <= H, W <= 100**
- **![](https://latex.codecogs.com/svg.image?1\leq&space;A_{i,j}&space;\leq&space;100)**

## Output Format

Print the required answer, i.e the price of the toy, in one line.

## Sample Input 0

```
1 1
1
```

## Sample Output 0

```
6
```

### Explanation 0

![](https://s3.amazonaws.com/hr-assets/0/1505569910-2f8fc5da13-3d.png)

The surface area of **![](https://latex.codecogs.com/svg.image?1&space;\times&space;1\times&space;1)** cube is 6.

## Sample Input 1

```
3 3
1 3 4
2 2 3
1 2 4
```

## Sample Output 1

```
60
```

### Explanation 1

![](https://s3.amazonaws.com/hr-assets/0/1509009918-091bdd4cba-1502631298-5cd3275ce9-img2.png)

The object is rotated so the front row matches column 1 of the input, heights 1, 2, and 1.

The front face is 1 + 2 + 1 = 4 units in area.
The top is 3 units.
The sides are 4 units.
None of the rear faces are exposed.
The underside is 3 units.
The front row contributes 4 + 3 + 4 + 3 = 14 units to the surface area.

---

## Solution

```javascript
/*
 * Complete the 'surfaceArea' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts 2D_INTEGER_ARRAY A as parameter.
 */

function surfaceArea(A) {
  // Write your code here
  let count = 0;

  for (let i = 0, itotal = A.length; i < itotal; i++) {
    for (let j = 0, jtotal = A[0].length; j < jtotal; j++) {
      count +=
        [
          (A[i - 1] && A[i - 1][j]) || 0,
          (A[i + 1] && A[i + 1][j]) || 0,
          A[i][j - 1] || 0,
          A[i][j + 1] || 0
        ].reduce((target, item) => target + Math.max(0, A[i][j] - item), 0) + 2;
    }
  }

  return count;
}
```
