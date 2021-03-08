---
title: "윈도우즈 설치 프로젝트"
permalink: /posts/install-project/
date: "2021-03-08 21:54:46 +0900"
categories:
  - visual studio
---
방탈 라이브러리 게임을 배포하기 위한 설치 프로젝트를 만든다.

## Installer Projects 확장
설치 프로젝트를 만들기 위해서는 "Microsoft Visual Studio Installer Projects" 확장을 설치해야 한다.
Visual Studio 확장(X)/확장 관리(M) 메뉴에서 "Microsoft Visual Studio Installer Projects"를
설치한다. Visual Studio를 종료하면 확장이 설치 된다.

<figure>
  <a href="/assets/images/visual_studio_installer_projects_extension.png">
  <img src="/assets/images/visual_studio_installer_projects_extension.png" alt="Installer Projects 확장"></a>
</figure>

## 설치 프로젝트 추가
솔루션을 선택하고 오른쪽 버튼 메뉴에서 새 프로젝트를 추가한다.
프로젝트 템플릿에서 Setup Project 템플릿으로 프로젝트를 추가한다.

<figure>
  <a href="/assets/images/visual_studio_create_installer_project.png">
  <img src="/assets/images/visual_studio_create_installer_project.png" alt="Installer Project 생성"></a>
</figure>

Examples 솔루션에 SantaRace 게임 프로젝트와 SantaRace_Installer라는 SantaRace 게임의
설치 프로젝트가 생성된 것을 확인할 수 있다.

<figure>
  <a href="/assets/images/visual_studio_create_installer_project2.png">
  <img src="/assets/images/visual_studio_create_installer_project2.png" alt="Installer Project 확인"></a>
</figure>

## 설치 프로젝트 구성

1. 먼저 Application Folder에 설치할 프로젝트의 출력을 포함한다.
  - Application Folder의 오른쪽 버튼 메뉴에서 프로젝트 출력을 추가한다.
  - 설치할 프로젝트를 선택한다.
    <figure>
      <a href="/assets/images/visual_studio_config_installer_project1.png">
      <img src="/assets/images/visual_studio_config_installer_project1.png" alt="Installer Project 구성1"></a>
    </figure>
2. 게임 실행을 위한 방탈 리소스를 추가한다.
  - Application Folder의 오른쪽 버튼 메뉴에서 Folder를 추가한다.
  - Folder의 이름을 res로 변경한다. res 폴더에 fonts 폴더도 추가한다.
    <figure>
      <a href="/assets/images/visual_studio_config_installer_project2.png">
      <img src="/assets/images/visual_studio_config_installer_project2.png" alt="Installer Project 구성2"></a>
    </figure>
  - res에서 오른쪽 버튼 메뉴에서 파일을 추가한다.
  - %BANGTAL_HOME%\res의 모든 파일을 추가한다. fonts도.
    <figure>
      <a href="/assets/images/visual_studio_config_installer_project3.png">
      <img src="/assets/images/visual_studio_config_installer_project3.png" alt="Installer Project 구성3"></a>
    </figure>
3. 마찬가지로 게임 실행을 위한 리소스를 추가한다.
    <figure>
      <a href="/assets/images/visual_studio_config_installer_project4.png">
      <img src="/assets/images/visual_studio_config_installer_project4.png" alt="Installer Project 구성4"></a>
    </figure>
4. 방탈 라이브러리의 DLL 파일을 추가한다.
   - %BANGTAL_HOME%\bin\*.dll을 Application Folder에 복사한다.
    <figure>
      <a href="/assets/images/visual_studio_config_installer_project5.png">
      <img src="/assets/images/visual_studio_config_installer_project5.png" alt="Installer Project 구성5"></a>
    </figure>
5. 바탕 화면과 프로그램 메뉴에 단축 아이콘을 생성한다.
   - 기본 출력 from SantaRace의 오른쪽 메뉴에서 Shortcut을 생성한다.
   - 생성된 Shortcut을 User's Desktop으로 옮긴다.
    <figure>
      <a href="/assets/images/visual_studio_config_installer_project6.png">
      <img src="/assets/images/visual_studio_config_installer_project6.png" alt="Installer Project 구성6"></a>
    </figure>
   - "Shortcut to 기본 출력..."을 원하는 이름("Santa Race")으로 변경한다.
   - 마찬가지 방법으로 User’s Programs Menu에 Shortcut을 생성한다.
    <figure>
      <a href="/assets/images/visual_studio_config_installer_project7.png">
      <img src="/assets/images/visual_studio_config_installer_project7.png" alt="Installer Project 구성7"></a>
    </figure>

## 설치 프로젝트 속성

속성 창에서 Manufacturer, ProductName, Version 등을 변경한다.
<figure>
  <a href="/assets/images/visual_studio_config_installer_project8.png">
  <img src="/assets/images/visual_studio_config_installer_project8.png" alt="Installer Project 구성8"></a>
</figure>

## 설치 프로젝트 빌드

Release 모드로 빌드하면 설치 파일을 만들어 준다.
<figure>
  <a href="/assets/images/visual_studio_build_installer_project.png">
  <img src="/assets/images/visual_studio_build_installer_project.png" alt="Installer Project 빌드"></a>
</figure>

## 참고
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)
- [https://github.com/bosornd/bangtal.cpp](https://github.com/bosornd/bangtal.cpp)
