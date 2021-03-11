---
title: "윈도우즈에서 UTF-8 설정하기"
permalink: /posts/windows-utf-8/
date: "2021-03-05 09:23:46 +0900"
categories:
  - visual studio
---
MS-Windows는 기본적으로 CP949 방식으로 한글을 지원한다.
따라서, 방탈 라이브러리처럼 UTF-8(CP65001)을 사용해야 하는 경우에 명령어 창에서
한글이 깨지는 문제가 있다. 제어판에서 UTF-8을 지원하도록 설정함으로써
해결할 수 있다.

활성 코드 페이지(CP)가 949인 상태에서 UTF-8로 작성된 소스 코드를
"more" 명령으로 보면 한글이 깨진다.
<figure>
  <a href="/assets/images/windows_utf-8_problem1.png">
  <img src="/assets/images/windows_utf-8_problem1.png" alt="윈도우즈에서 UTF-8 문제"></a>
</figure>

"chcp 65001" 명령으로 코드 페이지를 65001로 변경하면 한글이 깨지지 않는 것을 알 수 있다.
<figure>
  <a href="/assets/images/windows_utf-8_problem2.png">
  <img src="/assets/images/windows_utf-8_problem2.png" alt="윈도우즈에서 UTF-8 문제 해결"></a>
</figure>

## 제어판에서 설정하기
제어판(<img src="https://img.icons8.com/nolan/64/windows-10.png" width=25 />-R을 누르고 control을 실행한다)을 열어서 "날짜, 시간 또는 숫자 형식 변경"을 선택한다.
<figure>
  <a href="/assets/images/windows_control_language.png">
  <img src="/assets/images/windows_control_language.png" alt="윈도우즈 제어판"></a>
</figure>

국가 또는 지역의 관리자 옵션에서 "시스템 로캘 변경(C)"을 선택하면
"세계 언어 지원을 위해 Unicode UTF-8 사용"을 선택할 수 있다.
시스템을 재시작하면 기본 코드 페이지가 65001로 변경된다.
<figure>
  <a href="/assets/images/windows_utf-8.png">
  <img src="/assets/images/windows_utf-8.png" alt="윈도우즈 UTF-8 설정"></a>
</figure>

명령어 창이나 Visual Studio 등 대부분의 프로그램에서 정상적으로 동작하고 있지만,
Beta인 만큼 다른 프로그램에서 한글이 깨지는 문제가 발생할 수 있다.
따라서, 콘솔 입출력이나 디버깅의 목적에 따라 UTF-8 지원을 선택해서
사용하는 것이 좋다.

## 프로그래밍 가이드
다양한 환경에서 한글 문제가 없도록 하기 위해서는 다음 가이드를 따르는 것이 좋다.
- 파일 및 경로의 이름에는 한글/공백/특수 문자 등을 포함하지 않는다.
- 소스 코드를 포함한 텍스트 문서는 UTF-8(BOM)으로 저장한다.

## 문제점
"세계 언어 지원을 위해 Unicode UTF-8 사용"을 선택하면 다음과 같은 문제가 발생한다.

- 알집 설치 및 업데이트에서 다음과 같이 한글이 깨진다.
  <figure>
    <a href="/assets/images/alzip_utf-8.png">
    <img src="/assets/images/alzip_utf-8.png" alt="알집 설치 오류"></a>
  </figure>
- draw.io, plantuml 등에서 출력된 svg 파일을 MS-WORD에 삽입할 때 한글이 깨진다.
  <figure>
    <a href="/assets/images/word_utf-8.png">
    <img src="/assets/images/word_utf-8.png" alt="워드 오류"></a>
  </figure>
