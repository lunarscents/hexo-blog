---
title: 짝수와 홀수
thumbnail: '/images/programmers.png'
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
date: 2019-06-21 12:48:20
---

## 문제 설명
정수 num이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환하는 함수, solution을 완성해주세요.<br/>

<!-- more -->

## 제한 조건
- num은 int 범위의 정수입니다.
- 0은 짝수입니다.

<br/>

## 입출력 예

| arr | return |
| --- | --- |
| 3 | Odd |
| 4 | Even |

<br/>

### Solution

---

```javascript
function solution(num) {
    return num % 2 ? 'Odd' : 'Even';
}
```