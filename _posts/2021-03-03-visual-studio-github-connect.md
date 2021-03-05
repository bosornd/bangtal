---
title: "Visual Studio에서 GitHub 연동하기"
permalink: /posts/visual-studio-github-connect/
date: "2021-03-03 20:20:16 +0900"
categories:
  - git, visual studio
---
Visual Studio에서 GitHub와 연동해서 저장소를 관리할 수 있다.

## 프로젝트 생성하기
Visual Studio의 프로젝트 템플릿에서 콘솔 앱을 선택해서 프로젝트를 생성한다.
<figure>
  <a href="/assets/images/visual_studio_create_project.png">
  <img src="/assets/images/visual_studio_create_project.png" alt="콘솔 앱으로 프로젝트 생성하기"></a>
</figure>

## GitHub와 연결하기
Visual Studio 오른쪽 아래 "소스 제어에 추가" 메뉴가 있다. "Git(G)"을 선택해서 Git 서비스에 연동한다.
<figure>
  <a href="/assets/images/visual_studio_github1.png">
  <img src="/assets/images/visual_studio_github1.png" alt="GitHub 연동하기1"></a>
</figure>

"Publish to GitHub"를 선택해서 GitHub 저장소를 생성한다.
GitHub 계정이 연결되지 않은 경우에는 GitHub 계정을 연동해야 한다.
물론 계정이 없으면 계정을 생성해야 한다. [http://github.com](http://github.com)
<figure>
  <a href="/assets/images/visual_studio_github2.png">
  <img src="/assets/images/visual_studio_github2.png" alt="GitHub 연동하기2"></a>
</figure>

게시(생성)할 저장소(Repository) 정보를 입력한다.
그림은 GitHub 사이트의 Yongjin-Cho라는 계정에 Bangtal-Example이라는 저장소를 생성하고
게시한다. GitHub 링크도 확인한다.
<figure>
  <a href="/assets/images/visual_studio_github3.png">
  <img src="/assets/images/visual_studio_github3.png" alt="GitHub 연동하기3"></a>
</figure>

브라우저로 저장소가 생성되었음을 확인한다.
생성된 과제 파일이 GitHub에 잘 올라갔음을 확인할 수 있다.
<figure>
  <a href="/assets/images/visual_studio_github4.png">
  <img src="/assets/images/visual_studio_github4.png" alt="GitHub 연동하기4"></a>
</figure>

## 변경 사항 동기화 하기

이제 프로그램을 개발한다. "배경-1.png"로 "룸1"이라는 장면을 생성한다.
그리고, 게임을 시작한다. 빌드에도 문제가 없음을 알 수 있다.
<figure>
  <a href="/assets/images/visual_studio_program.png">
  <img src="/assets/images/visual_studio_program.png" alt=""></a>
</figure>

Git 변경 내용 탭에서 변경 내용을 확인한다. "Example.cpp"는 M(변경) 되었고,
"배경-1.png"는 A(추가) 되었음을 알 수 있다. 변경된 내용에 대한 설명을 입력한다.
그리고, "모두 커밋" 명령으로 저장을 준비한다.
<figure>
  <a href="/assets/images/visual_studio_github5.png">
  <img src="/assets/images/visual_studio_github5.png" alt="커밋 생성하기"></a>
</figure>

변경 사항을 저장소에 반영하기 위한 커밋(Commit)이 생성되었음을 알 수 있다.
커밋을 클릭하면 상세 내용을 확인할 수 있다.
위 방향의 버튼을 클릭하면 커밋 내용을 서버로 푸시(Push)할 수 있다.
<figure>
  <a href="/assets/images/visual_studio_github6.png">
  <img src="/assets/images/visual_studio_github6.png" alt="커밋 확인하기"></a>
</figure>

GitHub 저장소로 푸시되었음을 확인할 수 있다.
<figure>
  <a href="/assets/images/visual_studio_github7.png">
  <img src="/assets/images/visual_studio_github7.png" alt="푸시 확인하기"></a>
</figure>

브라우저로 저장소가 갱신되었음을 확인한다. "Example.cpp"가 수정되었으며,
"배경-1.png" 파일이 추가되었음을 알 수 있다.
<figure>
  <a href="/assets/images/visual_studio_github8.png">
  <img src="/assets/images/visual_studio_github8.png" alt="푸시 확인하기"></a>
</figure>
