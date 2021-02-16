---
title: "방탈출 만들기"
permalink: /docs/python/room-escape/
excerpt: "방탈출 만들기"
modified: "2021-02-16 16:00:00 +0900"
---
간단한 방탈출 게임을 통해 방탈 라이브러리를 배워보자.
설명에 사용된 이미지와 완성된 프로그램은 다음 링크를 참고한다.
- [https://github.com/bosornd/bangtal.python](https://github.com/bosornd/bangtal.python)

## 룸(장면)을 생성한다.

방탈 라이브러리를 사용하기 위해서는 bangtal 모듈을 포함해야 한다.<br />
그리고, Scene() 함수로 장면을 생성한다. 첫번째 파라미터는 장면의 이름이고,
두번째 파라미터는 장면의 배경 이미지다.
```python
from bangtal import *         // 방탈 라이브러리 모듈 포함하기

room1 = Scene("룸1", "Images/배경-1.png")
startGame(room1)
```

상기 프로그램은 Images 폴더에 있는 배경-1.png(이미지) 파일로 장면을 생성한다.
room1은 생성된 장면 객체를 가리키는 변수다.
startGame(room1) 함수로 room1에서부터 게임을 시작하도록 한다.<br />

<figure>
  <a href="/assets/images/create_room1.png">
  <img src="/assets/images/create_room1.png" alt="룸1 생성하기"></a>
</figure>

## 문(물체)을 생성한다.

방탈 라이브러리에서 물체는 Object() 함수로 생성한다.
```python
from bangtal import *

scene1 = Scene("룸1", "RoomEscape/배경-1.png")

door1 = Object("RoomEscape/문-오른쪽-열림.png")
door1.locate(scene1, 800, 270)
door1.show()

startGame(room1)
```
상기 프로그램은 문-오른쪽-열림.png(이미지) 파일로 물체를 생성한다.
Object.locate() 함수로 생성된 물체를 장면에 배치한다. door1을 room1의 (800, 270)에 위치시킨다.
방탈 라이브러리에서 좌표는 왼쪽 아래가 원점이며 x축은 오른쪽으로 y축은 위로 증가한다.<br />
Object.show() 함수로 물체를 장면에 보이게 한다.

<figure>
  <a href="/assets/images/create_door1.png">
  <img src="/assets/images/create_door1.png" alt="문1 생성하기"></a>
</figure>

## 문으로 나가면 게임을 종료한다.
사용자가 마우스로 문(물체)을 클릭하면 게임에서는 마우스 이벤트가 발생한다.
마우스 콜백 함수를 등록해서 발생한 이벤트를 처리할 수 있다.

```python
from bangtal import *

scene1 = Scene("룸1", "RoomEscape/배경-1.png")

door1 = Object("RoomEscape/문-오른쪽-열림.png")
door1.locate(scene1, 800, 270)
door1.show()

def door1_mouseCallback(x, y, action):
    endGame()
door1.onMouseAction = door1_mouseCallback

startGame(scene1)
```
마우스 이벤트를 처리하기 위한 함수(door1_mouseCallback)를 선언하고,
door1.onMouseAction에 저장한다.<br />

사용자가 문을 클릭하면 등록한 door1_mouseCallback() 함수가 호출된다.
이때 클릭한 물체의 포인터가 object로, 클릭한 위치가 (x, y) 좌표로, 클릭한 마우스 동작이
action으로 넘겨진다. endGame() 함수로 게임을 종료한다.

## 문을 열고 나간다.
닫혀 있는 문을 클릭하면 열리고, 열린 문을 클릭하면 게임을 종료하도록 해보자.
마우스 콜백 함수를 다음과 같이 수정한다.
```python
from bangtal import *

scene1 = Scene("룸1", "RoomEscape/배경-1.png")

door1 = Object("RoomEscape/문-오른쪽-닫힘.png")
door1.locate(scene1, 800, 270)
door1.show()
door1.closed = True

def door1_mouseCallback(x, y, action):
    if door1.closed:
        door1.setImage("RoomEscape/문-오른쪽-열림.png")
        door1.closed = False
    else:
        endGame()
door1.onMouseAction = door1_mouseCallback

startGame(scene1)
```
문이 닫혀 있는 가를 저장하는 변수(closed1)를 door1의 멤버로 설정한다.
사용자가 문을 클릭할 때마다 마우스 콜백 함수가 호출되는데,
이때 closed1 변수가 true이면
Object.setImage() 함수로 문 이미지를 열린 것으로 바꿔준다.\
그리고, closed1 변수를 false로 해서 문이 열려 있음을 저장한다.<br />

다시 문을 클릭하면 closed1이 false이므로 else 문이 실행되어 게임이 종료된다.

## 열쇠로 문 열기
열쇠를 가지고 있지 않으면 문이 열리지 않도록 해보자.<br />
먼저 열쇠(물체)를 생성해서 방(장면)에 위치시킨다.
```python
from bangtal import *

scene1 = Scene("룸1", "RoomEscape/배경-1.png")

key = Object("RoomEscape/열쇠.png")
key.setScale(0.2)
key.locate(scene1, 600, 150)
key.show()

def key_onMouseAction(x, y, action):
    key.pick()
key.onMouseAction = key_onMouseAction

startGame(scene1)
```
열쇠 이미지가 커서 Object.setScale() 함수로 크기를 줄여준다(20%).<br />

열쇠에 마우스 콜백 함수를 등록해서, 열쇠를 클릭하면 줍도록 한다.
Object.pick() 함수로 열쇠를 집는다. 열쇠를 집으면 인벤토리로 이동되며 사용하는 상태가 된다.

<figure>
  <a href="/assets/images/create_key.png">
  <img src="/assets/images/create_key.png" alt="열쇠 생성하기"></a>
</figure>

<figure>
  <a href="/assets/images/pick_key.png">
  <img src="/assets/images/pick_key.png" alt="열쇠 집기"></a>
</figure>

열쇠를 사용하고 있는 경우에만 문이 열리도록 door1의 마우스 콜백 함수를 수정하자.
```python
from bangtal import *

scene1 = Scene("룸1", "RoomEscape/배경-1.png")

door1 = Object("RoomEscape/문-오른쪽-닫힘.png")
door1.locate(scene1, 800, 270)
door1.show()
door1.closed = True

key = Object("RoomEscape/열쇠.png")
key.setScale(0.2)
key.locate(scene1, 600, 150)
key.show()

def onMouseAction_key(x, y, action):
    key.pick()
key.onMouseAction = onMouseAction_key

def door1_mouseCallback(x, y, action):
    if door1.closed:
        if key.inHand():
            door1.setImage("RoomEscape/문-오른쪽-열림.png")
            door1.closed = False
        else:
            showMessage("열쇠가 필요해~~~")
    else:
        endGame()
door1.onMouseAction = door1_mouseCallback

startGame(scene1)
```
Object.inHand() 함수로 열쇠(key)가 사용 중인지를 확인할 수 있다.
열쇠가 사용 중이 아니면 "열쇠가 필요해~~~"라는 메시지를 출력한다.

<figure>
  <a href="/assets/images/need_key.png">
  <img src="/assets/images/need_key.png" alt="열쇠가 필요하다는 메시지 출력하기"></a>
</figure>

showMessage() 함수로 메시지를 출력할 수 있다.
