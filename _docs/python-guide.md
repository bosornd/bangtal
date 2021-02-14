---
title: "Python Guide"
permalink: /docs/python-guide/
excerpt: "How to create a bangtal library game using Python on MS-Windows."
modified: "2021-02-14 17:51:00 +0900"
---
Visual Studio를 사용해서 방탈 라이브러리 게임을 만들 수 있다.

## Visual Studio 설치하기
먼저 최신 버전의 [Visual Studio](https://visualstudio.microsoft.com/ko/downloads/)를 다운 받아서 설치한다. 학생 및 오픈 소스 개발자를 위한 Community 버전을 설치한다.
- C/C++ 개발을 위해서 설치 항목에 "C++을 사용한 데스크톱 개발"을 선택한다.
- Python 개발을 위해서 설치 항목에 "Python 개발"을 선택한다. 32-bit 버전의 Python 개발 환경을 설치한다.

<figure>
  <a href="/images/visual_studio_install.png">
  <img src="/images/visual_studio_install.png" alt="Visual Studio Installer Options"></a>
</figure>

## Bangtal Library 설치하기
최신 버전의 방탈 라이브러리([Bangtal.msi](https://github.com/bosornd/bangtal/releases))를 설치한다.

## 프로젝트 생성하기
Visual Studio에서 파이썬 어플리케이션 프로젝트를 생성한다.
<figure>
  <a href="/images/python_create_project.png">
  <img src="/images/python_create_project.png" alt="파이썬 프로젝트 생성하기"></a>
</figure>

## 방탈 패키지 설치하기
도구(T)/Python(P)/Python 환경(E) 메뉴로 Python 환경 창을 연다. PyPI로부터 방탈 패키지를 설치한다.

<figure>
  <a href="/images/python_install_bangtal.png">
  <img src="/images/python_install_bangtal.png" alt="방탈 패키지 설치하기"></a>
</figure>

## 게임 프로그램 만들기
장면을 생성(createScene 함수)하고, 생성된 장면으로 게임을 시작(startGame 함수)해 본다.
PY 파일에 프로그램을 작성한다.

<figure>
  <a href="/images/python_program.png">
  <img src="/images/python_program.png" alt="게임 프로그램 만들기"></a>
</figure>

## 참고
- [https://github.com/bosornd/bangtal.python](https://github.com/bosornd/bangtal.python)
- [https://github.com/bosornd/bangtal.othello](https://github.com/bosornd/bangtal.othello)
