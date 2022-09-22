---
title: iPhone Safari Debugging 방법
categories:
  - Tools
  - Debug
tags:
  - Debug Tools
  - iPhone Safari Debugging 방법
  - Safari Debugging
  - Safari Technology Preview
  - Mobile web Debugging
  - 아이폰 사파리를 디버깅하는 방법
  - 모바일 웹 디버깅
thumbnail: /images/safaritechnologypreview.png
toc: true
date: 2021-09-01 20:21:50
---

모바일 Safari 브라우저는 MacOS 환경의 Safari 브라우저와 다른 동작 또는 화면을 보여주는 경우가 있습니다.
그래서 모바일 웹 브라우저 환경에서 개발을 진행할 때마다 모바일 Safari 브라우저에서 디버깅해야 합니다.
여기 모바일 Safari 브라우저 디버깅할 수 있는 방법을 소개합니다.

<!-- more -->

## Safari Technology Preview

MacOS 환경의 Safari 브라우저에서는 더 이상 디버깅 기능을 지원하지 않습니다.
이 기능을 대체할 수 있는 Safari Technology Preview 를 설치하면 디버깅 기능 사용이 가능합니다.

### Setup

- Safari Browser 에서 `Develop` > `Get Safari Technology Preview` 클릭 > 다운로드 페이지 접속하여 다운받아 설치하거나, homebrew 를 통해 설치할 수 있습니다.

{% gdemo_terminal 'brew install cask safari-technology-preview' '70px' 'zsh' '500' '$' 'terminal1' %}
{% endgdemo_terminal %}

---

## iPhone Simulator

iPhone Simulator 기능을 사용하면, 모바일 웹 브라우저를 디버깅을 할 수 있습니다.

### Xcode 설치

- Appstore에서 설치

### Simulator 실행

1. Xcode 실행 > 상단 메뉴 `Xcode` > `Open Developer Tool` > `Simulator`

{% asset_img "isd-1.png" "Simulator step 1" %}

2. Simulator 실행 > 상단 메뉴 `File` > `Open Simulator` > iOS [버전] > [디바이스 선택]

{% asset_img "isd-2.png" "Simulator step 2" %}

3. 선택한 디바이스 시뮬레이터가 실행됩니다.

{% asset_img "isd-3.png" "Simulator step 3" %}

{% blockquote %}
디바이스를 소지하고 있다면, USB 연결을 통해서도 debugging이 가능합니다.

디바이스 디버깅을 위해서는 Mac과 IPhone이 동일한 계정으로 로그인 되어있어야합니다.
{% endblockquote %}

---

## MobileWeb Safari 디버깅 방법

Simulator 에서 Safari 앱을 실행하여, 디버깅 타겟 사이트로 접속합니다.

- Safari Technology Preview 브라우저를 실행하고, 다음과 같이 `Develop > Simulator - iPhone …` 를 선택합니다. **→ 디버깅 가능한 Web Inspector가 실행된 것을 확인 할 수 있습니다.**

---

## References

- [Safari Technology Preview](https://developer.apple.com/safari/technology-preview/)
- [Mac Safari Technology Preview 설치 및 사용](https://rkatk1523.tistory.com/8)
