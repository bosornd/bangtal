---
title: "Visual Studio Guide"
permalink: /docs/visual-studio-guide/
excerpt: "How to create a bangtal library game using Visual Studio on MS-Windows."
modified: "2021-02-14 17:51:00 +0900"
---
Visual Studio를 사용해서 방탈 라이브러리 게임을 만들 수 있다.

## Visual Studio 설치
먼저 최신 버전의 [Visual Studio](https://visualstudio.microsoft.com/ko/downloads/)를 다운 받아서 설치한다. 학생 및 오픈 소스 개발자를 위한 Community 버전을 설치한다.
- C/C++ 개발을 위해서 설치 항목에 "C++을 사용한 데스크톱 개발"을 선택한다.
- Python 개발을 위해서 설치 항목에 "Python 개발"을 선택한다. 32-bit 버전의 Python 개발 환경을 설치한다.

<figure>
  <a href="/assets/images/visual_studio_install.png">
  <img src="/assets/images/visual_studio_install.png" alt="Visual Studio Installer Options"></a>
</figure>

## 방탈 라이브러리 설치
최신 버전의 방탈 라이브러리([Bangtal.msi](https://github.com/bosornd/bangtal/releases))를 설치한다.

## 프로젝트 생성
Visual Studio에서 콘솔 앱으로 프로젝트를 생성한다.
<figure>
  <a href="/assets/images/visual_studio_create_project.png">
  <img src="/assets/images/visual_studio_create_project.png" alt="콘솔 앱으로 프로젝트 생성하기"></a>
</figure>

## 게임 프로그램 생성
장면을 생성(createScene 함수)하고, 생성된 장면으로 게임을 시작(startGame 함수)해 본다.
CPP 파일에 프로그램을 작성한다.

<figure>
  <a href="/assets/images/visual_studio_program.png">
  <img src="/assets/images/visual_studio_program.png" alt="게임 프로그램 만들기"></a>
</figure>

## 설치 오류
정상적으로 설치되었으면 별도의 설정이 없이도 헤더 파일이나 라이브러리를 사용할 수 있다. 헤더 파일을 포함할 수 없어서 컴파일 오류가 발생하거나 라이브러리를 링크하면서 오류가 발생한다면 설치가 정상적 인지를 확인한다. 프로젝트 속성에 $(BANGTAL_HOME)include와 $(BANGTAL_HOME)lib가 포함되어 있는지 확인한다.

<figure>
  <a href="/assets/images/visual_studio_project_settings.png">
  <img src="/assets/images/visual_studio_project_settings.png" alt="Visual Studio 프로젝트 속성"></a>
</figure>

- 프로젝트 속성에 $(BANGTAL_HOME)include 등이 설정되지 않은 경우:  %localappdata%\Microsoft\MSBuild\v4.0\Microsoft.Cpp.Win32.user.props 파일에 Include/Library 경로가 설정되어 있는지를 확인한다.

```
<?xml version="1.0" encoding="utf-8"?>
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets">
  </ImportGroup>
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup>
    <IncludePath>$(BANGTAL_HOME)include;$(IncludePath)</IncludePath>
    <LibraryPath>$(BANGTAL_HOME)lib\win32\$(Configuration);$(LibraryPath)</LibraryPath>
  </PropertyGroup>
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

- 환경 변수 BANGTAL_HOME이 설정되지 않은 경우: 방탈 라이브러리가 설치된 경로로 설정한다.
<figure>
  <a href="/assets/images/windows_env_variable.png">
  <img src="/assets/images/windows_env_variable.png" alt="환경 변수 설정하기"></a>
</figure>

## 실행 오류1 (경로)
실행하면서 startGame()에서 오류가 발생했다면, 게임을 시작할 장면이 비정상적인 경우입니다.
대체로 이미지 경로가 잘못되어 createScene()에서 장면을 생성하는데 실패한 경우입니다.
이 경우에 createScene()의 반환이 0입니다(정상적인 경우에는 0이 아닌 자연수입니다).
<figure>
  <a href="/assets/images/visual_studio_debug_fault.png">
  <img src="/assets/images/visual_studio_debug_fault.png" alt="이미지 설정 오류"></a>
</figure>

이미지 경로는 Visual Studio에서 실행하는 경우에는 프로젝트 폴더를 기준으로 상대 경로입니다.
즉, "배경-1.png"는 프로젝트 폴더에 있어야 합니다. "Images/배경-1.png"는 프로젝트
폴더의 Images 폴더에 있어야 합니다.<br />
직접 실행 파일로 실행한 경우에는 실행 파일을 실행한 현재 경로를 기준으로
상대 경로에 이미지가 있어야 합니다.

## 실행 오류2 (한글)
방탈 라이브러리는 한글을 포함한 모든 문자열을 UTF-8로 인식한다. 따라서 소스 코드의 저장 방식도
UTF-8(BOM)이어야  한다. 다음과 같이 메모장에서 인코딩 방식을 확인할 수 있는데, 그냥
UTF-8이면 한글이 인식되지 않는다. UTF-8(BOM)으로 바꿔야 한다.
<figure>
  <a href="/assets/images/windows_korean_encoding1.png">
  <img src="/assets/images/windows_korean_encoding1.png" alt="인코딩 UTF-8"></a>
</figure>

파일(F) - 다른 이름으로 저장(A) 메뉴로 인코딩을 UTF-8(BOM)으로 변경해서 저장한다.
<figure>
  <a href="/assets/images/windows_korean_encoding2.png">
  <img src="/assets/images/windows_korean_encoding2.png" alt="인코딩 UTF-8(BOM)"></a>
</figure>

윈도우즈는 기본적으로 코드 페이지 949(ANSI)를 사용하지만,
웹, 안드로이드 등에서는 코드 페이지 65001(UTF-8)을 사용한다.
다양한 환경에서 공통적으로 사용하기 위해서는 UTF-8을 사용하는 것이 좋다.<br />
일반적으로 모든 파일명은 영문을 사용하는 것이 좋다.<br />
UTF-8을 사용하는 경우에 명령어 창 등에서 한글이 깨지는 문제가 발생할 수 있는데,
이는 시스템에서 UTF-8을 지원하도록 설정함으로써 해결할 수 있다. [링크](/posts/windows-utf-8/) 참조

## 참고
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)
- [https://github.com/bosornd/bangtal.cpp](https://github.com/bosornd/bangtal.cpp)
- [https://github.com/bosornd/bangtal.gogh](https://github.com/bosornd/bangtal.gogh)
- [https://github.com/bosornd/bangtal.othello](https://github.com/bosornd/bangtal.othello)
