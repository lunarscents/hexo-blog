---
title: Cavity Map
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
date: 2022-09-18 20:11:43
---

You are given a square map as a matrix of integer strings. Each cell of the map has a value denoting its depth. We will call a cell of the map a cavity if and only if this cell is not on the border of the map and each cell adjacent to it has strictly smaller depth. Two cells are adjacent if they have a common side, or edge.

Find all the cavities on the map and replace their depths with the uppercase character X.

<!-- more -->

## Example

**<p align="center">grid = ['989', '191', '111']</p>**

The grid is rearranged for clarity:

```
989
191
111
```

Return:

```
989
1X1
111
```

The center cell was deeper than those on its edges: [8,1,1,1]. The deep cells in the top two corners do not share an edge with the center cell, and none of the border cells is eligible.

## Function Description

Complete the cavityMap function in the editor below.

cavityMap has the following parameter(s):

string grid[n]: each string represents a row of the grid

## Returns

string{n}: the modified grid

## Input Format

The first line contains an integer , the number of rows and columns in the grid.

Each of the following lines (rows) contains positive digits without spaces (columns) that represent the depth at .

## Constraints

- 1 <= n <= 100

## Sample Input

```
STDIN   Function
-----   --------
4       grid[] size n = 4
1112    grid = ['1112', '1912', '1892', '1234']
1912
1892
1234
```

## Sample Output

```
1112
1X12
18X2
1234
```

## Explanation

The two cells with the depth of 9 are not on the border and are surrounded on all sides by shallower cells. Their values are replaced by X.

---

## Solution

### Solution 1 with JS

```javascript
/*
 * Complete the 'cavityMap' function below.
 *
 * The function is expected to return a STRING_ARRAY.
 * The function accepts STRING_ARRAY grid as parameter.
 */

function cavityMap(grid) {
  // Write your code here
  const cavities = grid.map(item => item.split(''));

  return cavities.reduce((target, list, index, source) => {
    const result = list
      .reduce((listTarget, item, itemIndex) => {
        listTarget.push(
          index >= 1 &&
            itemIndex >= 1 &&
            index < source.length - 1 &&
            itemIndex < list.length &&
            item > source[index][itemIndex - 1] &&
            item > source[index][itemIndex + 1] &&
            item > source[index - 1][itemIndex] &&
            item > source[index + 1][itemIndex]
            ? 'X'
            : item
        );

        return listTarget;
      }, [])
      .join('');

    target.push(result);

    return target;
  }, []);
}
```

### Solution 2 with TS

```typescript
/*
 * Complete the 'cavityMap' function below.
 *
 * The function is expected to return a STRING_ARRAY.
 * The function accepts STRING_ARRAY grid as parameter.
 */
function cavityMap(grid: string[]): string[] {
  // Write your code here
  const cavities: string[][] = grid.map(item => (item || '').split(''));

  return cavities.reduce((target, list, index, source) => {
    const result = list
      .reduce((listTarget, item, itemIndex) => {
        listTarget.push(
          index >= 1 &&
            itemIndex >= 1 &&
            index < source.length - 1 &&
            itemIndex < list.length &&
            item > source[index][itemIndex - 1] &&
            item > source[index][itemIndex + 1] &&
            item > source[index - 1][itemIndex] &&
            item > source[index + 1][itemIndex]
            ? 'X'
            : item
        );

        return listTarget;
      }, [] as string[])
      .join('');

    target.push(result);

    return target;
  }, [] as string[]);
}
```
