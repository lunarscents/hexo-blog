---
title: Strong Password
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
  - Strings
  - Strong Password of Algorithms hackerrank solution in javascript
thumbnail: /images/hackerrank.jpeg
date: 2022-10-04 08:30:00
---

Louise joined a social networking site to stay in touch with her friends. The signup page required her to input a name and a password. However, the password must be strong. The website considers a password to be strong if it satisfies the following criteria:

- Its length is at least **6**.
- It contains at least one digit.
- It contains at least one lowercase English character.
- It contains at least one uppercase English character.
- It contains at least one special character. The special characters are: `!@#$%^&*()-+`

She typed a random string of length **n** in the password field but wasn't sure if it was strong. Given the string she typed, can you find the minimum number of characters she must add to make her password strong?

Note: Here's the set of types of characters in a form you can paste in your solution:

```
numbers = "0123456789"
lower_case = "abcdefghijklmnopqrstuvwxyz"
upper_case = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
special_characters = "!@#$%^&*()-+"
```

<!-- more -->

## Example

**password = '2bbbb'**

This password is 5 characters long and is missing an uppercase and a special character. The minimum number of characters to add is **2**.

**password = '2bb#A'**

This password is 5 characters long and has at least one of each character type. The minimum number of characters to add is **1**.

## Function Description

Complete the minimumNumber function in the editor below.

minimumNumber has the following parameters:

- int n: the length of the password
- string password: the password to test

## Returns

- int: the minimum number of characters to add

## Input Format

The first line contains an integer **n**, the length of the password.

The second line contains the password string. Each character is either a lowercase/uppercase English alphabet, a digit, or a special character.

## Constraints

- **1 <= n <= 100**
- All characters in **password** are in [a-z], [A-Z], [0-9], or [!@#$%^&*()-+ ].

## Sample Input 0

```
3
Ab1
```

## Sample Output 0

```
3
```

## Explanation 0

She can make the password strong by adding **3** characters, for example, `$hk`, turning the password into `Ab1$hk` which is strong.

**2** characters aren't enough since the length must be at least **6**.

## Sample Input 1

```
11
#HackerRank
```

## Sample Output 1

```
1
```

## Explanation 1

The password isn't strong, but she can make it strong by adding a single digit.

---

## Solution

```javascript
/*
 * Complete the 'minimumNumber' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. STRING password
 */

function minimumNumber(n, password) {
  // Return the minimum number of characters to make the password strong
  let count = 4;

  [
    '0123456789',
    'abcdefghijklmnopqrstuvwxyz',
    'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
    '!@#$%^&*()-+'
  ].reduce((target, validator, index) => {
    Array.from(password).some(item =>
      validator.includes(item) ? count-- : null
    );

    return target;
  }, []);

  return Math.max(count, 6 - n);
}
```
