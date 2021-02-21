---
title: "3주차 - 프로그래밍 맛보기(2)"
permalink: /lectures/c/week03/
---
산타 레이스 게임 예제를 따라하면서 C언어 프로그래밍을 맛본다.
설명에 사용된 이미지와 완성된 프로그램은 다음 링크를 참고한다.
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)

<figure>
  <img src="/assets/images/santarace.png" alt="산타 레이스">
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

## 1. 장면 생성
{% include video id="zDKoWFQlnnQ" provider="youtube" %}

## 2. 종료 버튼
{% include video id="2AsmRczDa1s" provider="youtube" %}

## 3. 시작 버튼
{% include video id="Nu-jndodPZg" provider="youtube" %}

## 4. Play 버튼
{% include video id="8yHo3pYWhzs" provider="youtube" %}

## 5. createObject 함수 재정의
{% include video id="A9sgarjJDL0" provider="youtube" %}

## 6. 타이머
{% include video id="BEGbTSDu41E" provider="youtube" %}

## 7. 게임 재시작
{% include video id="uL8CpSaJfdE" provider="youtube" %}

## 8. 게임 시작/종료 함수
{% include video id="GQCMXJQEbiQ" provider="youtube" %}
