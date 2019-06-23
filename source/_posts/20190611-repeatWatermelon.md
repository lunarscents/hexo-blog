---
title: '수박수박수박수박수박수?'
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - Level1
  - JavaScript
  - ES6
date: 2019-06-11 00:04:05
---

## 문제 설명
길이가 n이고, 수박수박수박수....와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 수박수박을 리턴하고 3이라면 수박수를 리턴하면 됩니다.

<!-- more -->

## 제한 조건
- n은 길이 10,000이하인 자연수입니다.

<br/>


## 입출력 예
| n | return |
| --- | --- |
| 3 | 수박수 |
| 4 | 수박수박 |

<br/>


### Solution

---

```javascript
function solution(n) {
    return `${'수박'.repeat(Math.floor(n / 2))}${n % 2 ? '수' : ''}`;
}
```