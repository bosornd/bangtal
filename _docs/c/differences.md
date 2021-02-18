---
title: "틀린그림찾기"
permalink: /docs/c/differences/
excerpt: "틀린그림찾기"
modified: "2021-02-17 15:10:00 +0900"
---
틀린그림찾기 게임을 통해 방탈 라이브러리를 배워보자.
설명에 사용된 이미지와 완성된 프로그램은 다음 링크를 참고한다.
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)

<figure>
  <img src="/assets/images/differences.png" alt="틀린그림찾기">
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
{% include video id="6xJUQ8kLeeA" provider="youtube" %}

## 2. 게임 종료
{% include video id="S1hHo3abMYU" provider="youtube" %}

## 3. 첫번째 틀린 곳 처리
{% include video id="1jumbzKSQr8" provider="youtube" %}

## 4. 틀린 곳 체크하는 함수 만들기
{% include video id="TNBr-xpGpmo" provider="youtube" %}

## 5. 두번째 틀린 곳 처리
{% include video id="4SF349gWFJY" provider="youtube" %}

## 6. 틀린 곳 모두 처리
{% include video id="DvdcEMs79Kc" provider="youtube" %}

## 7. 배열 이용하기
{% include video id="RlqT0UgxXBY" provider="youtube" %}

## 8. 반복문
{% include video id="6gf7LbPICSY" provider="youtube" %}

## 9. 틀린 곳 모두 찾으면 게임 종료
{% include video id="FzZzY5NzmzA" provider="youtube" %}
