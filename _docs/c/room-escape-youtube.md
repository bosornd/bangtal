---
title: "방탈출 만들기(유투브)"
permalink: /docs/c/room-escape-youtube/
excerpt: "방탈출 만들기"
modified: "2021-02-17 10:50:00 +0900"
---
간단한 방탈출 게임을 통해 방탈 라이브러리를 배워보자.
설명에 사용된 이미지와 완성된 프로그램은 다음 링크를 참고한다.
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)

<figure>
  <img src="/assets/images/room_escape.png" alt="방탈출">
</figure>

아래 동영상은 이전 버전으로 설명하고 있어서 다음 사항에 차이가 있다.

- 별도의 게임 서버를 띄우지 않는다.
- 헤더파일명이 변경되었다. Bangtal.h --> bangtal.h
- bangtal.h에 library 포함이 명시되어 있으므로
  별도로 명시하지 않아도 된다. #pragma comment(lib, "Bangtal.lib") 제거
- Object 이름이 제거되었다.
  createObject("문1", "Images/문-오른쪽-닫힘.png")
  --> createObject("Images/문-오른쪽-닫힘.png")
- 파일 경로를 입력할 때는 "\\"보다 "/"를 사용하는 것이 좋다.
  안드로이드 버전과의 호환성을 위함.
  기본 문자열이 UTF-8로 설정됨. #pragma execution_character_set("utf-8")
- keypad type이 제거되었다.
  암호에 따라서 영문/숫자가 자동으로 보인다.
  암호가 입력된 경우에 EVENT_KEYPAD가 발생하며 object callback으로 전달된다.
  별도의 keypad callback은 사용하지 않는다.

## 1. 장면을 생성한다.
{% include video id="DR17awoWyCs" provider="youtube" %}

## 2. 게임을 시작한다.
{% include video id="c6oNo4YnEEc" provider="youtube" %}

## 3. 문을 생성한다.
{% include video id="c00sVR32cg4" provider="youtube" %}

## 4. 문을 클릭하면 게임이 종료된다.
{% include video id="2di_FmlBhCc" provider="youtube" %}

## 5. 문1을 클릭하면 게임을 종료한다.
{% include video id="0A-T1FWHIY8" provider="youtube" %}

## 6. 문1을 열고 나간다.
{% include video id="X-RDACdkOZQ" provider="youtube" %}

## 7. 두개의 방을 나간다.
{% include video id="UBdt-a1WNk8" provider="youtube" %}

## 8. 열쇠를 사용한다.
{% include video id="yafbCfUJRE8" provider="youtube" %}

## 9.열쇠를 숨긴다.
{% include video id="sGGpYs0Yk-k" provider="youtube" %}

## 10. 키패드를 사용한다.
{% include video id="KxwlE84m_fQ" provider="youtube" %}

## 11. 방이 어두워지면 암호가 보인다.
{% include video id="8Rhob1e5Y00" provider="youtube" %}
