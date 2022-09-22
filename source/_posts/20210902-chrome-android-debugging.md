---
title: Chrome으로 Android Debugging 방법
categories:
  - Tools
  - Debug
tags:
  - Debug Tools
  - Chrome으로 Android Debugging 방법
  - Android Debugging
  - Android Debug Bridge
  - Mobile web Debugging
  - 안드로이드 디버깅하는 방법
  - 모바일 웹 디버깅
  - 안드로이드 디버그 브리지
thumbnail: /images/adb.png
toc: true
date: 2021-09-02 20:00:00
---

Android 디바이스의 모바일 브라우저 환경과 PC Chrome 브라우저에서는 서로 다르게 동작하거나, 다르게 화면이 보이는 경우가 있습니다.
매번 배포한 후 디바이스에서 테스트하는 것은 시간이 많이 소요되며, 빠르게 이슈 파악하여 대응하기 어려워지기도 합니다.
여기 PC에서 Android 디바이스의 브라우저를 디버깅할 수 있는 방법을 소개합니다.

<!-- more -->

## Requirements

### USB 케이블

- 데이터 전송 케이블 (충전 케이블 :dizzy_face:)

{% blockquote %}
충전 케이블이 아니라 데이터 전송 케이블로 연결해야합니다.
{% endblockquote %}

### Android 개발자 모드 설정

1. Android Device > `설정` > `휴대전화 정보` > `소프트 웨어 정보` > [빌드번호] 7번 터치
2. Android Device > `설정` > `개발자 옵션` > `USB 디버깅 활성화` 선택

{% asset_img "cad-1.png" "app1" %}
{% asset_img "cad-2.png" "app2" %}

### ADB 설치

Android SDK에 포함된 `ADB(Android Debug Bridge)` 를 설치해야합니다.

- Chrome 확장 프로그램으로 ![ADB](https://chrome.google.com/webstore/detail/adb/dpngiggdglpdnjdoaefidgiigpemgage)를 설치

---

## How to Debugging

### ADB 실행

- PC 크롬 브라우저를 실행 시켜 설치한 ADB 확장 프로그램을 실행합니다.

{% asset_img "cad-3.png" "adb1" %}
{% asset_img "cad-4.png" "adb2" %}

- `Discover USB devices` 가 체크되어 있는 지 확인합니다.

### PC와 Android 디바이스 USB 연결

Android 디바이스와 PC를 USB 케이블로 연결합니다.

- 디바이스에서 `USB 디버깅을 허용하겠습니까?` 라는 확인 창이 뜨면 `허용` 을 선택합니다.

{% asset_img "cad-5.png" "app3" %}

- PC 크롬 브라우저에서 `chrome://inspect#devices` 창을 새로 고침을 합니다.
  연결된 디바이스의 모바일 브라우저 리스트가 아래와 같이 표시된다.

{% asset_img "cad-6.png" "adb3" %}

- 디바이스 브라우저 항목 밑의 `inspect` 를 클릭하여 디버깅 한다.

{% asset_img "cad-7.png" "adb4" %}

---

## References

- [Remote debug Android devices - Chrome Developers](https://developer.chrome.com/docs/devtools/remote-debugging/)
- [PC 크롬 브라우저로 Android 기기 브라우저 디버깅하기](https://velog.io/@dev-song/PC-%ED%81%AC%EB%A1%AC-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EB%A1%9C-Android-%EA%B8%B0%EA%B8%B0-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80-%EB%94%94%EB%B2%84%EA%B9%85%ED%95%98%EA%B8%B0)
- [크롬으로 안드로이드 디바이스 디버깅 하기](https://kure0406.tistory.com/54)
