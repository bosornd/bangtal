---
title: "Python Guide"
permalink: /docs/python-guide/
excerpt: "How to create a bangtal library game using Python on MS-Windows."
modified: "2021-02-14 17:51:00 +0900"
---
Visual Studio를 사용해서 Python으로 방탈 라이브러리 게임을 만들 수 있다.

## Visual Studio 설치하기
먼저 최신 버전의 [Visual Studio](https://visualstudio.microsoft.com/ko/downloads/)를 다운 받아서 설치한다. 학생 및 오픈 소스 개발자를 위한 Community 버전을 설치한다.
- C/C++ 개발을 위해서 설치 항목에 "C++을 사용한 데스크톱 개발"을 선택한다.
- Python 개발을 위해서 설치 항목에 "Python 개발"을 선택한다. 32-bit 버전의 Python 개발 환경을 설치한다.

<figure>
  <a href="/assets/images/visual_studio_install.png">
  <img src="/assets/images/visual_studio_install.png" alt="Visual Studio Installer Options"></a>
</figure>

## Bangtal Library 설치하기
최신 버전의 방탈 라이브러리([Bangtal.msi](https://github.com/bosornd/bangtal/releases))를 설치한다.

## 프로젝트 생성하기
Visual Studio에서 파이썬 어플리케이션 프로젝트를 생성한다.
<figure>
  <a href="/assets/images/python_create_project.png">
  <img src="/assets/images/python_create_project.png" alt="파이썬 프로젝트 생성하기"></a>
</figure>

## 방탈 패키지 설치하기
도구(T)/Python(P)/Python 환경(E) 메뉴로 Python 환경 창을 연다. PyPI로부터 방탈 패키지를 설치한다. pip install bangtal 명령.

<figure>
  <a href="/assets/images/python_install_bangtal.png">
  <img src="/assets/images/python_install_bangtal.png" alt="방탈 패키지 설치하기"></a>
</figure>

## 게임 프로그램 만들기
장면을 생성(createScene 함수)하고, 생성된 장면으로 게임을 시작(startGame 함수)해 본다.
PY 파일에 프로그램을 작성한다.

<figure>
  <a href="/assets/images/python_program.png">
  <img src="/assets/images/python_program.png" alt="게임 프로그램 만들기"></a>
</figure>

## Visual Studio 사용하지 않기
VIsual Studio를 사용하지 않고 다른 IDE를 사용하거나 명령어 창에서 직접 방탈 프로그램을 실행할 수도 있다.
단, x86용 Python 3.7을 사용해야 한다(상위 버전이나 x64용에서는 방탈 라이브러리가 정상적으로 동작하지 않는다).
현재 최신 버전은 [3.7.9](https://www.python.org/ftp/python/3.7.9/python-3.7.9.exe)이다.

<figure>
  <a href="/assets/images/python_download.png">
  <img src="/assets/images/python_download.png" alt="파이썬 설치 파일"></a>
</figure>

설치할 때 Python을 경로에 추가하도록 설정하는 것이 좋다.

<figure>
  <a href="/assets/images/python_install.png">
  <img src="/assets/images/python_install.png" alt="파이썬 경로 추가"></a>
</figure>

다음과 같이 명령어 창에서 python을 실행하고 직접 프로그래밍 할 수 있다.
물론 방탈 라이브러리([Bangtal.msi](https://github.com/bosornd/bangtal/releases))가 설치되어야 하며
Python 방탈 패키지도 설치되어야 한다(pip install bangtal 명령).

<figure>
  <a href="/assets/images/python_console.png">
  <img src="/assets/images/python_console.png" alt="콘솔에서 파이썬 프로그래밍1"></a>
</figure>

또한 Python 기본 IDE인 IDLE에서 프로그램을 작성하고 실행시킬 수 있습니다(F5 Run Module 명령으로).
또는 명령창에서 파일로 직접 실행할 수도 있다.

<figure>
  <a href="/assets/images/python_console2.png">
  <img src="/assets/images/python_console2.png" alt="콘솔에서 파이썬 프로그래밍2"></a>
</figure>

## 실행 파일 만들기
pyinstaller로 실행 파일을 만들 수 있다. 먼저 pip install pyinstaller 명령으로 pyinstaller를 설치한다.
그리고, 다음 명령으로 Python 프로그램을 실행 파일로 만들 수 있다.
```
pyinstaller --add-data "%BANGTAL_HOME%/bin/bangtal.dll;." --add-data "%BANGTAL_HOME%/res;res" --add-data "*.png;." -w example.py
```
--add-data 옵션으로 실행에 필요한 파일을 포함할 수 있다.<br />
-w 옵션은 콘솔창이 보이지 않도록 한다.<br />
pyinstaller가 프로그램에 필요한 bangtal.dll을 자동으로 포함하는데,
파일명이 bangtal.dll에서 bangtal로 바뀐다. 이 문제로 bangtal.dll을 포함하도록 설정한다.

## 참고
- [https://github.com/bosornd/bangtal.python](https://github.com/bosornd/bangtal.python)
- [https://github.com/bosornd/bangtal.othello](https://github.com/bosornd/bangtal.othello)
