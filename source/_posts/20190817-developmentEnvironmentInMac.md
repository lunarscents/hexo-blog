---
title: Mac OS 개발 환경 설정 Guide
categories:
  - Tools
  - Development Environment
tags:
  - Tools
  - Development Environment in MacOS
toc: true
thumbnail: /images/macOS.jpg
date: 2019-08-17 23:50:37
---

## Overview

처음 MacOS 환경에서 접하는 FrontEnd 개발자 분들에게 개발 환경을 설정하는 방법을 소개하려 합니다.
이 글을 통해 기본적인 설정을 쉽게 진행해보시기 바랍니다. (macOS Mojave 기준)

<!-- more -->

## System Setting

### Finder 숨김 폴더 및 파일 노출 설정

- Finder 에서 숨겨진 폴더 또는 파일을 보여주거나 숨기고 싶을 때 아래와 같은 단축키로 제어할 수 있습니다.
- `command` + `shift` + `.`

### Finder 기본 폴더 설정

- Finder 실행 시 기본 폴더를 Home 폴더로 설정합니다.
- `General` > `New Finder windows show`:  (home folder)

### 파일 확장자 보여주기

- 모든 파일의 확장자를 보여주는 설정은 아래와 같습니다.
- `Advanced` > `Show all filename extensions`: 체크하세요.

<br/>

---

## Requirements

개발 환경 구축을 위한 필수 프로그램을 설치합니다.

### Xcode

macOS에서 `gcc`, `make` 같은 컴파일 도구를 사용하려면 기본적으로 Homebrew 또는 명령어 라인 도구(Command Line Tools)을 먼저 설치해야 합니다.

Command Line Tools는 Xcode를 설치하면 자동으로 같이 설치됩니다.

하지만, Xcode 용량이 크고 모든 사람이 IDE가 필요한 게 아니므로 명령어 도구만 따로 설치하겠습니다.

<br/>

{% gdemo_terminal 'xcode-select --install' '70px' 'zsh' '500' '$' 'demo-teriminal1' %}
{% endgdemo_terminal %}

<br/>

### Homebrew

{% blockquote %}
macOS 용 패키지 관리자
{% endblockquote %}

<br/>

- [Homebrew](https://brew.sh/)

#### Brew 설치

Terminal을 실행 시켜 아래 명령어를 복사하여 붙여넣기 해주세요.

{% gdemo_terminal '/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"' '70px' 'zsh' '500' '$' 'demo-teriminal1' %}
{% endgdemo_terminal %}

<br/>

#### Brew cask

Command Line에서 명령어로 여러가지 맥용 어플리케이션을 설치하게 해주는 유틸리티 입니다.

1. `설치가 간편하다`
    - 기존 설치 방법대로, 앱스토어나 해당 사이트에 접속하여 설치 파일을 다운받고 실행 시켜 마우스로 이동 할 필요없이 커맨드라인에서 간편하게 설치 가능합니다.

{% gdemo_terminal 'brew tap caskroom/cask;brew tap caskroom/versions;brew tap caskroom/fonts;brew tap homebrew/dupes;' '70px' 'zsh' '500' '$' 'demo-teriminal2-1' %}
{% endgdemo_terminal %}


2. `설치목록을 저장하여 재설치를 자동화 할 수 있다.`
    - 새로운 기기나 환경에서 설치하거나 재설치 할 경우 목록만 있으면 많은 어플리케이션을 한번에 설치 할 수 있다.
    - 아쉽게도 앱스토어에만 있는 어플들은 이렇게 설치하지 못합니다.

{% gdemo_terminal 'brew cask list > app_list.txt;brew cask install $(cat app_list.txt)' '70px' 'zsh' '500' '$' 'demo-teriminal2-2' %}
{% endgdemo_terminal %}


### git 설치

Version 관리 도구로 macOS에 기본으로 설치되어 있지만 최신 버전이 아니므로 brew를 이용하여 업데이트 합니다.

<br/>

{% gdemo_terminal 'brew install git' '70px' 'zsh' '500' '$' 'demo-teriminal3-1' %}
{% endgdemo_terminal %}

<br/>

{% gdemo_terminal 'git config --global user.name <Your Name>' '70px' 'zsh' '500' '$' 'demo-teriminal3-2' %}
{% endgdemo_terminal %}

<br/>

{% gdemo_terminal 'git config --global user.email <you@your-domain.com>' '70px' 'zsh' '500' '$' 'demo-teriminal3-3' %}
{% endgdemo_terminal %}

<br/>

---

## iTerm2 설치

[iTerm2](https://www.iterm2.com/downloads.html) 는 기본 터미널에 기능을 확장한 무료 애플리케이션입니다.

macOS에 기본으로 설치되어 있는 Terminal 대신 iTerm2를 터미널 앱으로 사용합니다. 

<br/>

{% gdemo_terminal 'brew cask install iterm2' '70px' 'zsh' '500' '$' 'demo-teriminal4' %}
{% endgdemo_terminal %}

<br/>


## zsh 설치

macOS 의 기본 shell은 bash 를 대체할 zsh를 설치합니다.

macOS Catalina 부터 zsh을 기본 shell로 지원합니다.

<br/>

{% blockquote %}
Zsh is a shell designed for interactive use, although it is also a powerful scripting language. Many of the useful features of bash, ksh, and tcsh were incorporated into zsh; many original features were added.
{% endblockquote %}

<br/>

1. `컨텍스트 기반 자동완성 기능(tab)`
2. `다양하고 예쁜 테마와 플러그인`
3. `스펠링 체크`
4. `history 기능`

<br/>

{% gdemo_terminal 'brew install zsh;chsh -s $(which zsh)' '70px' 'zsh' '500' '$' 'demo-teriminal5' %}
{% endgdemo_terminal %}

<br/>

## oh-my-zsh 설치

Oh my zsh 를 이용해서 테마와 플러그인들을 적용할 수 있습니다.

또한, zsh 의 기능을 확장시켜주고 편리한 개발 환경을 도와 줍니다.

<br/>

{% blockquote %}
Oh-My-Zsh is an open source, community-driven framework for managing your ZSH configuration. It comes bundled with a ton of helpful functions, helpers, plugins, themes, and a few things that make you shout…
{% endblockquote %}

<br/>

{% gdemo_terminal 'sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"' '70px' 'zsh' '500' '$' 'demo-teriminal6' %}
{% endgdemo_terminal %}

<br/>

### oh-my-zsh 테마 변경

oh-my-zsh에서 제공하는 [Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/themes) 를 확인하고 `~/.zshrc`를 열고 테마명을 지정해주면 테마를 설정 할 수 있습니다.

<br/>

{% gdemo_terminal 'ZSH_THEME="robbyrussell" # 기본 테마' '70px' 'zsh' '500' '$' 'demo-teriminal6' %}
{% endgdemo_terminal %}

<br/>

---

## 필요한 어플리케이션 설치

1. Alfred

[alfred](https://www.alfredapp.com/)는 독특한 단축키와 키스트로크 시스템을 통해 생산성을 높여줍니다.
 
- 앱을 실행하고 파일을 찾고 계산하는 것은 물론 빠르고 정확하게 맥을 제어할 수 있습니다. 
- 사용자 설정 기능도 강력합니다. 
- MacOS의 단점인 스폿라이트(spotlight)를 훌륭하게 보완한 앱입니다.

<br/>

{% gdemo_terminal 'brew cask install alfred//brew install alfred' '70px' 'zsh' '500' '$' 'demo-teriminal7' %}
{% endgdemo_terminal %}

<br/>

2. Divvy

[divvy](https://mizage.com/divvy/)는 사용자가 화면을  창의 크기와 위치를 내 마음대로 한번에 조절이 가능합니다.

- free trial version 을 사용합니다.

set PATH - 패스설정 실행


### 이어서 ..


### 필요한 어플리케이션 설치

1. alfred

2. divvy

3. git

{% gdemo_terminal 'brew cask install google-chrome' '70px' 'zsh' '500' '$' 'demo-teriminal1-2' %}
{% endgdemo_terminal %}

{% gdemo_terminal 'brew cask install firefox' '70px' 'zsh' '500' '$' 'demo-teriminal1-3' %}
{% endgdemo_terminal %}

{% gdemo_terminal 'brew install git' '70px' 'zsh' '500' '$' 'demo-teriminal1-4' %}
{% endgdemo_terminal %}



## NVM 설치 및 설정

## SSH

## Tips

1. defaults write com.apple.finder AppleShowAllFiles -bool true
2. killall Finder (파인더 강제 종료)
3. cheat sheet
http://www.mediaatelier.com/CheatSheet/
단축키