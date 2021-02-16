---
title: "방탈출 만들기"
permalink: /docs/c++/room-escape/
excerpt: "방탈출 만들기"
modified: "2021-02-16 14:50:00 +0900"
---
간단한 방탈출 게임을 통해 방탈 라이브러리를 배워보자.
설명에 사용된 이미지와 완성된 프로그램은 다음 링크를 참고한다.
- [https://github.com/bosornd/bangtal.cpp](https://github.com/bosornd/bangtal.cpp)

## 룸(장면)을 생성한다.

방탈 라이브러리를 사용하기 위해서는 bangtal을 포함해야 한다.
C언어에서 사용하는 bangtal.h는 포함하지 않아도 된다.
그리고, bangtal namespace를 사용한다.<br />
그리고, [Scene::create()](/api/classbangtal_1_1_scene.html#a3ad3e0db50cac0a549f7342e28d33f7c) 함수로
장면을 생성한다. 첫번째 파라미터는 장면의 이름이고, 두번째 파라미터는 장면의 배경 이미지다.
```c++
#include <bangtal>            // 방탈 라이브러리를 사용하기 위한 헤더 포함하기
using namespace bangtal;      // bangtal 네임 스페이스를 사용한다고 선언하기

int main()
{
	auto room1 = Scene::create("룸1", "Images/배경-1.png");
	startGame(room1);
}
```

C/C++ 프로그램은 main() 함수에서 시작한다.
상기 프로그램은 Images 폴더에 있는 배경-1.png(이미지) 파일로 장면을 생성하고,
생성된 장면으로 게임을 시작한다.
[startGame()](/api/namespacebangtal.html#a8eb706a2a0ed55817c95ef990086d99b) 함수로 게임을 시작한다.<br />
여기서 room1은 정보(값)를 저장하는 [변수](https://ko.wikipedia.org/wiki/변수_(컴퓨터 과학))다.
C/C++에서 변수를 선언하기 위해서는 자료형이 있어야 하는데, auto는 저장된 값에 따라서 자료형이 결정된다.
room1의 자료형은
[Scene::create()](/api/classbangtal_1_1_scene.html#a3ad3e0db50cac0a549f7342e28d33f7c)
함수로 생성되는 장면 객체의
포인터([ScenePtr](/api/namespacebangtal.html#abb35c3c750f71093eb016b9d812066e3))이다.
ScenePtr room1으로 선언한 것과 동일하다.

<figure>
  <a href="/assets/images/create_room1.png">
  <img src="/assets/images/create_room1.png" alt="룸1 생성하기"></a>
</figure>

## 문(물체)을 생성한다.

방탈 라이브러리에서 물체는 [Object::create()](/api/classbangtal_1_1_object.html#a8acd0706b38dce38fe14971bca3d2b5f)
함수로 생성한다.
```c++
#include <bangtal>
using namespace bangtal;

int main()
{
	auto room1 = Scene::create("룸1", "Images/배경-1.png");
	auto door1 = Object::create("Images/문-오른쪽-열림.png", room1, 800, 270);

	startGame(room1);
}
```
상기 프로그램은 문-오른쪽-열림.png(이미지) 파일로 물체를 생성한다.
생성된 물체를 room1의 (800, 270)에 위치시킨다.
방탈 라이브러리에서 좌표는 왼쪽 아래가 원점이며 x축은 오른쪽으로 y축은 위로 증가한다.

<figure>
  <a href="/assets/images/create_door1.png">
  <img src="/assets/images/create_door1.png" alt="문1 생성하기"></a>
</figure>

## 문으로 나가면 게임을 종료한다.
사용자가 마우스로 문(물체)을 클릭하면 게임에서는 마우스 이벤트가 발생한다.
마우스 콜백 함수를 등록해서 발생한 이벤트를 처리할 수 있다.

```c++
#include <bangtal>
using namespace bangtal;

bool door1_mouseCallback(ObjectPtr object, int x, int y, MouseAction action)
{
	endGame();

	return true;
}

int main()
{
	auto room1 = Scene::create("룸1", "Images/배경-1.png");
	auto door1 = Object::create("Images/문-오른쪽-열림.png", room1, 800, 270);
	door1->setOnMouseCallback(door1_mouseCallback);

	startGame(room1);
}
```
마우스 이벤트를 처리하기 위한 함수(door1_mouseCallback)를 선언한다.
[Object::setOnMouseCallback()](/api/classbangtal_1_1_object.html#a819900bf45f0829982cd2ab9de307641) 함수로
선언한 마우스 콜백 함수를 게임 시스템에 등록한다.<br />

사용자가 문을 클릭하면 등록한 door1_mouseCallback() 함수가 호출된다.
이때 클릭한 물체의 포인터가 object로, 클릭한 위치가 (x, y) 좌표로, 클릭한 마우스 동작이
action으로 넘겨진다.
[endGame()](/api/bangtal_8h.html#aeda119595fcc834db9cfec532a90cf79) 함수로
게임을 종료한다.
<p />
콜백 함수는 시스템에 등록되면 자동으로 호출되며, 다른 곳에서는 사용하지 않는다.
따라서 이름 없는 함수로 만들어서 등록할 수 있다.
C++에서 이름 없는 함수 객체를
[람다 함수](https://en.cppreference.com/w/cpp/language/lambda)라고 한다.<br />
다음과 같이 람다 함수를 사용해서 마우스 콜백을 등록할 수 있다.

```c++
#include <bangtal>
using namespace bangtal;

int main()
{
	auto room1 = Scene::create("룸1", "Images/배경-1.png");
	auto door1 = Object::create("Images/문-오른쪽-열림.png", room1, 800, 270);
	door1->setOnMouseCallback([](auto object, auto x, auto y, auto action) -> bool {
		endGame();
		return true;
	});

	startGame(room1);
}
```
람다 함수는 []로 시작한다.
다음 (auto object, auto x, auto y, auto action)는 함수의 파라미터,
-> bool은 함수의 반환을 의미한다. 여기도 MouseCallback으로 등록하는 함수이므로
auto로 자료형을 선언할 수 있다.

## 문을 열고 나간다.
닫혀 있는 문을 클릭하면 열리고, 열린 문을 클릭하면 게임을 종료하도록 해보자.
마우스 콜백 함수를 다음과 같이 수정한다.
```c++
#include <bangtal>
using namespace bangtal;

int main()
{
	auto room1 = Scene::create("룸1", "Images/배경-1.png");
	auto door1 = Object::create("Images/문-오른쪽-닫힘.png", room1, 800, 270);
	auto closed1 = true;
	door1->setOnMouseCallback([&](auto object, auto x, auto y, auto action) -> bool {
		if (closed1) {
			object->setImage("Images/문-오른쪽-열림.png");
			closed1 = false;
		}
		else {
			endGame();
		}
		return true;
	});

	startGame(room1);
}
```
문이 닫혀 있는 가를 저장하는 변수(closed1)를 선언한다.
사용자가 문을 클릭할 때마다 마우스 콜백 함수가 호출되는데,
이때 closed1 변수가 true이면
[Object::setImage()](/api/classbangtal_1_1_object.html#a9bf28ee253ffaaad4bb25e9beb80c70b) 함수로
문 이미지를 열린 것으로 바꿔준다. 그리고, closed1 변수를 false로 해서 문이 열려 있음을 저장한다.<br />

다시 문을 클릭하면 closed1이 false이므로 else 문이 실행되어 게임이 종료된다.

## 열쇠로 문 열기
열쇠를 가지고 있지 않으면 문이 열리지 않도록 해보자.<br />
먼저 열쇠(물체)를 생성해서 방(장면)에 위치시킨다.
```c++
#include <bangtal>
using namespace bangtal;

int main()
{
	auto room1 = Scene::create("룸1", "Images/배경-1.png");
	auto door1 = Object::create("Images/문-오른쪽-닫힘.png", room1, 800, 270);
	auto closed1 = true;
	door1->setOnMouseCallback([&](auto object, auto x, auto y, auto action) -> bool {
		if (closed1) {
			object->setImage("Images/문-오른쪽-열림.png");
			closed1 = false;
		}
		else {
			endGame();
		}
		return true;
	});

	auto key = Object::create("Images/열쇠.png", room1, 600, 150);
	key->setScale(0.2f);
	key->setOnMouseCallback([&](auto object, auto x, auto y, auto action) -> bool {
		object->pick();
		return true;
	});


	startGame(room1);
}
```
열쇠 이미지가 커서
[Object::setScale()](/api/classbangtal_1_1_object.html#aeb5f1aba5c856072368001103f78711e) 함수로
크기를 줄여준다(20%).<br />

열쇠에 마우스 콜백 함수를 등록해서, 열쇠를 클릭하면 줍도록 한다.
[Object::pick()](/api/classbangtal_1_1_object.html#a2b7d74354b53fff7a8ef913b2e1eb020) 함수로
열쇠를 집는다. 열쇠를 집으면 인벤토리로 이동되며 사용하는 상태가 된다.

<figure>
  <a href="/assets/images/create_key.png">
  <img src="/assets/images/create_key.png" alt="열쇠 생성하기"></a>
</figure>

<figure>
  <a href="/assets/images/pick_key.png">
  <img src="/assets/images/pick_key.png" alt="열쇠 집기"></a>
</figure>

열쇠를 사용하고 있는 경우에만 문이 열리도록 door1의 마우스 콜백 함수를 수정하자.
```c++
#include <bangtal>
using namespace bangtal;

int main()
{
	auto room1 = Scene::create("룸1", "Images/배경-1.png");
	auto door1 = Object::create("Images/문-오른쪽-닫힘.png", room1, 800, 270);
	auto closed1 = true;

	auto key = Object::create("Images/열쇠.png", room1, 600, 150);
	key->setScale(0.2f);
	key->setOnMouseCallback([&](auto object, auto x, auto y, auto action) -> bool {
		object->pick();
		return true;
	});

	door1->setOnMouseCallback([&](auto object, auto x, auto y, auto action) -> bool {
		if (closed1) {
			if (key->isHanded()) {
				object->setImage("Images/문-오른쪽-열림.png");
				closed1 = false;
			}
			else {
				showMessage("열쇠가 필요해~~~");
			}
		}
		else {
			endGame();
		}
		return true;
	});

	startGame(room1);
}
```
[Object::isHanded()](/api/classbangtal_1_1_object.html#ae1776922c90a3fc51d4b70d0e4d8ce2a) 함수로
열쇠(key)가 사용 중인지를 확인할 수 있다.
열쇠가 사용 중이 아니면 "열쇠가 필요해~~~"라는 메시지를 출력한다.

<figure>
  <a href="/assets/images/need_key.png">
  <img src="/assets/images/need_key.png" alt="열쇠가 필요하다는 메시지 출력하기"></a>
</figure>

[showMessage()](/api/namespacebangtal.html#a97a439a0bf46cf493cfeaa9e03f7fd2b) 함수로
메시지를 출력할 수 있다.
