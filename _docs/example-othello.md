---
title: "예제: 오델로"
permalink: /docs/example-othello/
excerpt: "오델로 예제"
modified: "2021-02-14 20:51:00 +0900"
---
- [https://github.com/bosornd/bangtal.othello](https://github.com/bosornd/bangtal.othello)

C++ 방탈 라이브러리로 개발되었으며,
동일한 소스 코드로 Windows (Visual Studio) / Android (Android Studio) / MacBook (Xcode) 프로젝트를 구성한다.
Python 프로젝트도 포함되어 있다.

## 게임 소개

[오델로](https://ko.wikipedia.org/wiki/오델로)는 가로 세로 8칸의 보드에
검은 돌과 흰돌을 번갈아 놓는 보드 게임이다.
돌은 반드시 상대방 돌을 양쪽으로 포위하여 뒤집을 수 있는 곳에만 놓을 수 있다.

<figure>
  <img src="/assets/images/othello_game2.png">
</figure>

간단한 컴퓨터 플레이어도 구현되어 있어서<br />
사람 vs. 컴퓨터 또는 컴퓨터 vs 컴퓨터도 게임을 즐길 수 있다.

<figure>
  <img src="/assets/images/othello_game1.png">
</figure>

## 실행 파일 만들기
pyinstaller를 사용해서 Python 프로그램을 실행 파일로 만들 수 있다.
먼저 pyinstaller를 설치한다(pip install pyinstaller).
그리고, 다음 명령으로 실행 파일을 생성할 수 있다.

```
pyinstaller othello.spec
```

그 전에 config.py에 IAMGE_PATH를 "Image/"로 수정해야 한다.

방탈 라이브러리 설치 폴더가 "C:\Program Files (x86)\Bosornd\Bangtal\"이 아닌 경우에
othello.spec을 수정해야 한다.
