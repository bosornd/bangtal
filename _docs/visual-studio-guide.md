---
title: "Visual Studio Guide"
permalink: /docs/visual-studio-guide/
excerpt: "How to create a bangtal library game using Visual Studio on MS-Windows."
modified: "2021-02-14 17:51:00 +0900"
---
Visual Studio를 사용해서 방탈 라이브러리 게임을 만들 수 있다.

## Visual Studio 설치하기
먼저 최신 버전의 [Visual Studio](https://visualstudio.microsoft.com/ko/downloads/)를 다운 받아서 설치한다. 학생 및 오픈 소스 개발자를 위한 Community 버전을 설치한다.
- C/C++ 개발을 위해서 설치 항목에 "C++을 사용한 데스크톱 개발"을 선택한다.
- Python 개발을 위해서 설치 항목에 "Python 개발"을 선택한다. 32-bit 버전의 Python 개발 환경을 설치한다.

<figure>
  <img src="/images/visual_studio_install.png" alt="Visual Studio Installer Options">
</figure>

## Bangtal Library 설치하기
최신 버전의 방탈 라이브러리([Bangtal.msi](https://github.com/bosornd/bangtal/releases))를 설치한다.

## 프로젝트 생성하기
Visual Studio에서 콘솔 앱으로 프로젝트를 생성한다.
<figure>
  <img src="/images/visual_studio_create_project.png" alt="콘솔 앱으로 프로젝트 생성하기">
</figure>

## 게임 프로그램 만들기
장면을 생성(createScene 함수)하고, 생성된 장면으로 게임을 시작(startGame 함수)해 본다.
CPP 파일에 프로그램을 작성한다.

<figure>
  <img src="/images/visual_studio_program.png" alt="게임 프로그램 만들기">
</figure>

## 설치 오류
정상적으로 설치되었으면 별도의 설정이 없이도 헤더 파일이나 라이브러리를 사용할 수 있다. 프로젝트 속성에 $(BANGTAL_HOME)include와 $(BANGTAL_HOME)lib가 포함되어 있음을 확인할 수 있다.

<figure>
  <img src="/images/visual_studio_project_settings.png" alt="Visual Studio 프로젝트 속성">
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
  <img src="/images/windows_env_variable.png" alt="환경 변수 설정하기">
</figure>

## 참고
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)
- [https://github.com/bosornd/bangtal.cpp](https://github.com/bosornd/bangtal.cpp)
- [https://github.com/bosornd/bangtal.gogh](https://github.com/bosornd/bangtal.gogh)
- [https://github.com/bosornd/bangtal.othello](https://github.com/bosornd/bangtal.othello)
