---
title: "2주차 - 프로그래밍 맛보기(1)"
permalink: /lectures/c/week02/
---
간단한 방탈출 게임 예제를 따라하면서 C언어 프로그래밍을 맛본다.
설명에 사용된 이미지와 완성된 프로그램은 다음 링크를 참고한다.
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)

## 룸(장면)을 생성한다.

방탈 라이브러리를 사용하기 위해서는 bangtal.h을 포함해야 한다.
그리고, [createScene()](/api/bangtal_8h.html#a3b2c14502ab6ce66c317b12308915234) 함수로
장면을 생성한다.
첫번째 파라미터는 장면의 이름이고, 두번째 파라미터는 장면의 배경 이미지다.
```c++
#include <bangtal.h>    // 방탈 라이브러리를 사용하기 위한 헤더 포함하기

int main()
{
  SceneID room1 = createScene("룸1", "배경-1.png");
  startGame(room1);
}
```

C/C++ 프로그램은 main() 함수에서 시작한다.
상기 프로그램은 배경-1.png(이미지) 파일로 장면을 생성하고, 생성된 장면으로 게임을 시작한다.
[startGame()](/api/bangtal_8h.html#a4426589c4897d66f1af5e856056a33a7) 함수로 게임을 시작한다.
여기서 room1은 정보(값)를 저장하는 [변수](https://ko.wikipedia.org/wiki/변수_(컴퓨터 과학))이며 [SceneID](/api/bangtal_8h.html#a4276516c60e90dcc61adda40ef8dd0e5)는 room1의 [자료형](https://ko.wikipedia.org/wiki/자료형)이다.

<figure>
  <a href="/assets/images/create_room1.png">
  <img src="/assets/images/create_room1.png" alt="룸1 생성하기"></a>
</figure>

## 문(물체)을 생성한다.

방탈 라이브러리에서 물체는 [createObject()](/api/bangtal_8h.html#a0e7f05670de47ad24a63591b69bbe793)
함수로 생성한다.
```c++
#include <bangtal.h>

int main()
{
	SceneID room1 = createScene("룸1", "배경-1.png");

	ObjectID door1 = createObject("문-오른쪽-열림.png");
	locateObject(door1, room1, 800, 270);
	showObject(door1);

	startGame(room1);
}
```
상기 프로그램은 문-오른쪽-열림.png(이미지) 파일로 물체를 생성한다. [locateObject()](/api/bangtal_8h.html#a841791c660e8b5781662fbaf28620182) 함수로 생성된 물체를 장면에 배치한다.
door1을 room1의 (800, 270)에 위치시킨다.
방탈 라이브러리에서 좌표는 왼쪽 아래가 원점이며 x축은 오른쪽으로 y축은 위로 증가한다.<br />
[showObject()](/api/bangtal_8h.html#ae46082fc3da39525de3691944049afd5) 함수로
물체를 장면에 보이게 한다.

<figure>
  <a href="/assets/images/create_door1.png">
  <img src="/assets/images/create_door1.png" alt="문1 생성하기"></a>
</figure>

## 문으로 나가면 게임을 종료한다.
사용자가 마우스로 문(물체)을 클릭하면 게임에서는 마우스 이벤트가 발생한다.
마우스 콜백 함수를 등록해서 발생한 이벤트를 처리할 수 있다.

```c++
#include <bangtal.h>

void mouseCallback(ObjectID object, int x, int y, MouseAction action)
{
	endGame();
}

int main()
{
	setMouseCallback(mouseCallback);

	SceneID room1 = createScene("룸1", "배경-1.png");

	ObjectID door1 = createObject("문-오른쪽-열림.png");
	locateObject(door1, room1, 800, 270);
	showObject(door1);

	startGame(room1);
}
```
마우스 이벤트를 처리하기 위한 함수(mouseCallback)를 선언한다.
[setMouseCallback()](/api/bangtal_8h.html#a9b828a65e91609a44cd7e2ec8456e3b0) 함수로
선언한 마우스 콜백 함수를 게임 시스템에 등록한다.<br />

사용자가 문을 클릭하면 등록한 mouseCallback() 함수가 호출된다.
이때 클릭한 물체의 ID가 object로, 클릭한 위치가 (x, y) 좌표로, 클릭한 마우스 동작이
action으로 넘겨진다.<br />

[endGame()](/api/bangtal_8h.html#aeda119595fcc834db9cfec532a90cf79) 함수로
게임을 종료한다.

## 문을 열고 나간다.
닫혀 있는 문을 클릭하면 열리고, 열린 문을 클릭하면 게임을 종료하도록 해보자.
마우스 콜백 함수를 다음과 같이 수정한다.
```c++
#include <bangtal.h>

bool closed1 = true;
void mouseCallback(ObjectID object, int x, int y, MouseAction action)
{
	if (closed1) {
		setObjectImage(object, "문-오른쪽-열림.png");
		closed1 = false;
	}
	else {
		endGame();
	}
}

int main()
{
	setMouseCallback(mouseCallback);

	SceneID room1 = createScene("룸1", "배경-1.png");

	ObjectID door1 = createObject("문-오른쪽-닫힘.png");
	locateObject(door1, room1, 800, 270);
	showObject(door1);

	startGame(room1);
}
```
문이 닫혀 있는 가를 저장하는 변수(closed1)를 [전역 변수](https://ko.wikipedia.org/wiki/전역_변수)로 선언한다. 함수 내부에 선언되는 지역 변수는 함수 내에서만 접근이 가능하고, 함수가 반환되면 변수도 소멸된다.<br />

사용자가 문을 클릭할 때마다 mouseCallback() 함수가 호출되는데,
이때 closed1 변수가 true이면
[setObjectImage()](/api/bangtal_8h.html#a24c292b7d1ab92d00f10d75c06db3f48) 함수로
문 이미지를 열린 것으로 바꿔준다. 그리고, closed1 변수를 false로 해서 문이 열려 있음을 저장한다.<br />

다시 문을 클릭하면 closed1이 false이므로 else 문이 실행되어 게임이 종료된다.

## 열쇠로 문 열기
열쇠를 가지고 있지 않으면 문이 열리지 않도록 해보자.<br />
먼저 열쇠(물체)를 생성해서 방(장면)에 위치시킨다. main() 함수를 다음과 같이 변경한다.
이때 ObjectID door1과 key도 mouseCallback() 함수에서도 사용할 수 있도록
전역 변수로 선언한다.

```c++
SceneID room1;
ObjectID door1, key;
bool closed1 = true;

int main()
{
	setMouseCallback(mouseCallback);

	room1 = createScene("룸1", "배경-1.png");

	door1 = createObject("문-오른쪽-닫힘.png");
	locateObject(door1, room1, 800, 270);
	showObject(door1);

	key = createObject("열쇠.png");
	locateObject(key, room1, 600, 150);
	scaleObject(key, 0.2f);
	showObject(key);

	startGame(room1);
}
```
열쇠 이미지가 커서
[scaleObject()](/api/bangtal_8h.html#a0c607e8241b4d3293c69b813ad9771ad) 함수로
크기를 줄여준다(20%).

<figure>
  <a href="/assets/images/create_key.png">
  <img src="/assets/images/create_key.png" alt="열쇠 생성하기"></a>
</figure>

열쇠를 클릭하면 줍도록 해보자. 마찬가지로 마우스 콜백 함수를 수정해야 한다.

```c++
#include <bangtal.h>

SceneID room1;
ObjectID door1, key;
bool closed1 = true;

void mouseCallback(ObjectID object, int x, int y, MouseAction action)
{
	if (object == key) {
		pickObject(key);
	}
}
```
마우스 이벤트가 발생한 물체(object)가 key이면
[pickObject()](/api/bangtal_8h.html#a1f4f4b2856928a0bdf29609ee81f510d) 함수로
열쇠를 집는다. 열쇠를 집으면 인벤토리로 이동되며 사용하는 상태가 된다.

<figure>
  <a href="/assets/images/pick_key.png">
  <img src="/assets/images/pick_key.png" alt="열쇠 집기"></a>
</figure>

열쇠를 사용하고 있는 경우에만 문이 열리도록 해보자.
```c++
#include <bangtal.h>

SceneID room1;
ObjectID door1, key;
bool closed1 = true;

void mouseCallback(ObjectID object, int x, int y, MouseAction action)
{
	if (object == key) {
		pickObject(key);
	}
	else if (object == door1) {
		if (closed1) {
			if (key == getHandObject()) {
				setObjectImage(object, "문-오른쪽-열림.png");
				closed1 = false;
			}
			else {
				showMessage("열쇠가 필요해~~~");
			}
		}
		else {
			endGame();
		}
	}
}
```
마우스 이벤트가 발생한 물체(object)가 열쇠이면 집는다.<br />
열쇠가 아니고 door1인 경우에,<br />
문이 닫혀 있으면(closed1이 true이면)
사용하고 있는 물체가 열쇠이면 문을 열린 상태로 만든다. 이때,
[getHandObject()](/api/bangtal_8h.html#a548f9a09e6eee1f6c6963b658e05fc62) 함수로
사용하고 있는 물체의 ID를 알 수 있다.<br />
사용하고 있는 물체가 열쇠가 아니면 "열쇠가 필요해~~~"라는 메시지를 출력한다.

<figure>
  <a href="/assets/images/need_key.png">
  <img src="/assets/images/need_key.png" alt="열쇠가 필요하다는 메시지 출력하기"></a>
</figure>

[showMessage()](/api/bangtal_8h.html#aa3d14543ea624c7209e4cd2a9d33cb7a) 함수로
메시지를 출력할 수 있다.

## 동영상 강의
자세한 설명은 다음 동영상 강의를 참고하세요.
- [방탈출 게임 만들기 동영상](/docs/c/room-escape-youtube/)
