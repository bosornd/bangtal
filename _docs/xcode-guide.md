---
title: "Xcode Guide"
permalink: /docs/xcode-guide/
excerpt: "How to create a bangtal library game using Xcode on MacBook."
modified: "2021-02-14 19:41:00 +0900"
---
Xcode를 사용해서 방탈 라이브러리 게임을 만들 수 있다.

## Xcode 설치하기
먼저 Apple Store에서 최신 버전의 Xcode를 설치한다.

<figure>
  <img src="/images/xcode_install.png" alt="Apple Store에서 Xcode 설치하기">
</figure>

## Bangtal Library 설치하기
최신 버전의 방탈 라이브러리([Bangtal.pkg](https://github.com/bosornd/bangtal/releases))를 설치한다.

## 프로젝트 생성하기
- macOS 프로젝트를 "Command Line Tool"로 생성한다.
<figure>
  <img src="/images/xcode_create_project1.png" alt="프로젝트 생성하기">
</figure>

- Language를 C++로 설정한다. (Objective-C로 선택해도 상관 없지만...)
<figure>
  <img src="/images/xcode_create_project2.png" alt="프로그래밍 언어 C++ 선택하기">
</figure>

## 방탈 라이브러리를 포함하기
- 방탈 라이브러리(libbangtal.dylib)를 포함한다. Add Other File에서 설치된 라이브러리를 찾아서 추가 한다.
<figure>
  <img src="/images/xcode_add_library.png" alt="방탈 라이브러리 포함하기">
</figure>

- 방탈 라이브러리(libbangtal.dylib)의 헤더 파일 경로를 추가한다.
<figure>
  <img src="/images/xcode_add_header_path.png" alt="방탈 라이브러리 헤더 포함하기">
</figure>

## 게임 프로그램 만들기
장면을 생성(createScene 함수)하고, 생성된 장면으로 게임을 시작(startGame 함수)해 본다.
CPP 파일에 프로그램을 작성한다.
프로그래밍 언어를 Objective-C로 선택한 경우, main.m이 생성되는데, 이를 main.cpp로 변경해서 작성한다.

<figure>
  <img src="/images/xcode_program.png" alt="게임 프로그램 만들기">
</figure>

## 리소스 추가하기
빌드가 완료되면 게임에 사용되는 이미지 등을 복사하도록 설정합니다.

<figure>
  <img src="/images/xcode_resources.png" alt="리소스 추가하기">
</figure>

## 참고
- [https://github.com/bosornd/bangtal.xcode](https://github.com/bosornd/bangtal.xcode)
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)
- [https://github.com/bosornd/bangtal.cpp](https://github.com/bosornd/bangtal.cpp)
- [https://github.com/bosornd/bangtal.gogh](https://github.com/bosornd/bangtal.gogh)
- [https://github.com/bosornd/bangtal.othello](https://github.com/bosornd/bangtal.othello)
