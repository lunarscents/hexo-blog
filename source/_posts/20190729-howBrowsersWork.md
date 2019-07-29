---
title: '브라우저 동작 원리'
categories:
  - Front-end
  - Basic
tags:
  - Front-end
  - Basic for Web
toc: true
thumbnail: '/images/browsers.png'
date: 2019-07-29 15:39:30
---

## What is a Browser?
웹 브라우저는 인터넷 망에서 웹(www)서비스를 이용할 수 있게 하여 정보를 검색하고 정보를 볼 수 있게 해주는 응용프로그램 입니다.
<br/>

<!-- more -->

### 브라우저의 핵심 기능
브라우저의 주요 기능은 사용자가 참조하고자 하는 웹페이지를 서버에 요청(Request)하고 서버의 응답(Response)을 받아 브라우저에 표시하는 것입니다.

1. 브라우저는 서버로부터 HTML, CSS, Javascript, 이미지 파일 등을 응답받습니다.

2. HTML, CSS 파일은 렌더링 엔진의 HTML 파서와 CSS 파서에 의해 파싱(Parsing)되어 DOM, CSSDOM 트리로 변환되고 렌더 트리로 결합됩니다.

3. 이렇게 생성된 렌더 트리를 기반으로 브라우저는 웹페이지를 표시합니다.

{% asset_img "client-server.png" "how browsers work" %}

<br/>

### 브라우저의 기본 구조
1. `User Interface(사용자 인터페이스)`
    - 주소 표시줄, 이전/다음 버튼, 북마크 메뉴 등 요청한 페이지를 보여주는 창을 제외한 나머지 모든 부분입니다.
    
2. `Browser Engine(브라우저 엔진)`
    - 사용자 인터페이스와 렌더링 엔진 사이의 동작을 제어합니다.
    
3. `Rendering Engine(렌더링 엔진)`
    - 요청한 콘텐츠를 표시합니다. 예를 들어 HTML을 요청하면 HTML과 CSS를 파싱하여 화면에 표시합니다.
   
4. `Networking(통신)`
    - HTTP 요청과 같은 네트워크 호출에 사용합니다. 플랫폼 독립적인 인터페이스이며 각 플랫폼 하부에서 실행합니다.
    
5. `UI Backend(UI 백엔드)`
    - 콤보 박스와 창 같은 기본적인 장치를 그립니다. 플랫폼에서 명시하지 않은 일반적인 인터페이스로서, OS 사용자 인터페이스 체계를 사용합니다.
    
6. `JavaScript Interpreter(자바스크립트 해석기)`
    - 자바스크립트 코드를 해석하고 실행합니다.
    
7. `Data Persistence(자료 저장소)`
    - 자료를 저장하는 계층입니다. 쿠키를 저장하는 것과 같이 모든 종류의 자원을 하드 디스크에 저장할 필요가 있으며, HTML5 명세에는 브라우저가 지원하는 웹 데이터 베이스가 정의되어 있습니.


- `Chrome은 다른 브라우저와 달리 각 탭마다 별도의 렌더링 엔진 인스턴스를 유지하여 독립된 프로세스로 처리됩니다.`

<br/>

{% asset_img "layers.png" "Browser components" %}

---

## 렌더링 엔진 
렌더링 엔진은 요청 받은 내용을 브라우저 화면에 표시하는 일을 합니다.

<br/>

### 렌더링 엔진들
- Gecko 엔진 사용 : Firefox
- Webkit 엔진 사용 : Chrome, Safari

### 렌더링 엔진 기본 흐름
1. 웹 브라우저는 HTML(문자열)을 읽어 약속된 규칙을 기반으로 화면에 그립니다.(Rendering)

2. 그리기 위한 부가정보(CSS)를 주입시킬 수 있습니다.

3. 브라우저는 HTML을 브라우저가 다루기 편한 형태로 가공하여 관리합니다.(DOM)

4. DOM을 접근하고 조작할 수 있는 방법을 JavaScript API 형태로 제공합니다.

<br/>

{% asset_img "flow.png" "Rendering engine basic flow" %}

---

## 브라우저가 지원하지 않는 것
- 브라우저는 파일 시스템을 제공하지 않는다.
- JavaScript는 모듈 시스템을 제공하지 않는다.
- HTML은 정해진 UI를 포함한 컴포넌트를 제공하나 표준적인 확장 방법을 제공하지 않는다.

---

## Reference Site
- [How Browsers work](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)
- [렌더링 트리 생성, 레이아웃 및 페인트](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction?hl=ko)
- [브라우저는 어떻게 동작하는가?(번역)](https://d2.naver.com/helloworld/59361)
- [Poiemaweb의 브라우저 동작 원리](https://poiemaweb.com/js-browser)
