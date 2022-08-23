---
title: "API 가이드"
permalink: /docs/c/api-guide/
---

 다음 문장을 포함함으로써 [Bangtal API](/api/bangtal_8h.html)를 사용할 수 있다.

 ```c
 #include <bangtal.h>
 ```

## 게임 관련 함수
1. void [startGame](/api/bangtal_8h.html#a4426589c4897d66f1af5e856056a33a7)([SceneID](/api/bangtal_8h.html#a4276516c60e90dcc61adda40ef8dd0e5) scene)<br />
  scene으로부터 게임을 시작한다.
  scene으로 들어가면서 이벤트(EVENT_ENTER_SCENE)가 발생한다.

2. void [enterScene](/api/bangtal_8h.html#ab7bd17e48f38a77dcb37627368f732ad)([SceneID](/api/bangtal_8h.html#a4276516c60e90dcc61adda40ef8dd0e5) scene)<br />
  scene으로 전환한다.
  이전 scene에서 나오면서 이벤트(EVENT_LEAVE_SCENE)가 발생하고,
  scene으로 들어가면서 이벤트(EVENT_ENTER_SCENE)가 발생한다.

3. void [endGame](/api/bangtal_8h.html#aeda119595fcc834db9cfec532a90cf79)()<br />
  게임을 종료한다.

## 장면(Scene) 관련 함수
1. [SceneID](/api/bangtal_8h.html#a4276516c60e90dcc61adda40ef8dd0e5) [createScene](/api/bangtal_8h.html#a3b2c14502ab6ce66c317b12308915234)(const char* name, const char* image = nullptr)<br />
  주어진 이름(name)과 배경 이미지(image)를 가진 장면을 생성하고 ID를 반환한다.
  ```c
  SceneID scene1 = createScene("룸1", "Images/배경-1.png");
  ```

2. void [setSceneImage](/api/bangtal_8h.html#abad66ab1d22ffe375556f675a0d0e925)([SceneID](/api/bangtal_8h.html#a4276516c60e90dcc61adda40ef8dd0e5) scene, const char* image = nullptr)<br />
  장면(scene)의 배경 이미지(image)를 변경한다.
  ```c
  setSceneImage(scene1, "Images/배경-2.png");
  ```

3. void [setSceneLight](/api/bangtal_8h.html#acd2cad132b69e20d2da49ecc9703e1e8)([SceneID](/api/bangtal_8h.html#a4276516c60e90dcc61adda40ef8dd0e5) scene, SceneLight light)<br />
  장면(scene)의 밝기(light)를 조정한다. light는 0~1 사이의 float 값이다.
  ```c
  setSceneLight(scene1, 0.5f);      // 50%
  ```

4. void [setSceneCallback](/api/bangtal_8h.html#a01cb8d8c3db5ca59dae883ca3890850c)([SceneCallback](/api/bangtal_8h.html#a1c79e880a8b61c16f168a235da3f6303) callback)<br />
  장면에서 발생하는 이벤트를 수신하는 callback 함수를 설정한다.
  장면에 들어갈 때(EVENT_ENTER_SCENE), 나올 때(EVENT_LEAVE_SCENE) 이벤트가 발생한다.

## 물체(Object) 관련 함수
1. [ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) [createObject](/api/bangtal_8h.html#a0e7f05670de47ad24a63591b69bbe793)(const char* image)<br />
  주어진 이미지(image)로 믈체를 생성하고 ID를 반환한다.
  ```c
  ObjectID door1 = createObject("Images/문-오른쪽-닫힘.png");
  ```

2. void [setObjectImage](/api/bangtal_8h.html#a24c292b7d1ab92d00f10d75c06db3f48)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object, const char* image)<br />
  물체(object)의 이미지(image)를 변경한다.
  ```c
  setObjectImage(door1, "Images/문-오른쪽-열림.png");
  ```

3. void setObjectText([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object, const char* text = "")<br />
  물체(object)의 텍스트(text)를 변경한다.
  ```c
  setObjectText(door1, "한글 ABC\n123456");
  ```

4. void [locateObject](/api/bangtal_8h.html#a841791c660e8b5781662fbaf28620182)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object, [SceneID](/api/bangtal_8h.html#a4276516c60e90dcc61adda40ef8dd0e5) scene, int x, int y)<br />
  물체(object)를 장면(scene)에 위치(x, y)시킨다.
  ```c
  locateObject(door1, scene1, 800, 270);
  ```

5. void [scaleObject](/api/bangtal_8h.html#a0c607e8241b4d3293c69b813ad9771ad)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object, ObjectScale scale)<br />
  물체(object)의 크기(scale)를 조정한다.
  ```c
  scaleObject(door1, 2.f);            // 200%
  ```

6. void [showObject](/api/bangtal_8h.html#ae46082fc3da39525de3691944049afd5)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object) / void [hideObject](/api/bangtal_8h.html#ae02df98d7480b3e5788999b82f9cb251)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object)<br />
  물체(object)를 보이거나(showObject) 숨긴다(hideObject)
  ```c
  showObject(door1);
  ```

7. void [pickObject](/api/bangtal_8h.html#a1f4f4b2856928a0bdf29609ee81f510d)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object) / void [dropObject](/api/bangtal_8h.html#a290f97199c0fec4dd692726a44d25d26)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object)<br />
  물체(object)를 줍거나(pickObject) 떨어 뜨린다(dropObject)
  ```c
  pickObject(key);
  ```

8. void [defineCombination](/api/bangtal_8h.html#adf36922421459dddc9a574e0e22a2950)([ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object1, [ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object2, [ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object3)<br />
  물체의 조합 방법을 정의한다.
  object1과 object2를 조합(Combine)하면 object3가 된다.
  반대로 object3를 분해(Dismantle)하면 object1과 object2가 된다.

9. [ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) [getHandObject](/api/bangtal_8h.html#a548f9a09e6eee1f6c6963b658e05fc62)()<br />
  현재 사용하고 있는 물체의 ID가 반환된다.
  사용하고 있는 물체가 없으면 0이 반환된다.

10. void [setObjectCallback](/api/bangtal_8h.html#aa26bedd9fbedb7726135d8d870a80793)([ObjectCallback](/api/bangtal_8h.html#aae00ada60f57d513d22e752d0a3b78b5) callback)<br />
  물체에서 발생하는 이벤트를 수신하는 callback 함수를 설정한다.
  물체를 주울 때(EVENT_PICK_OBJECT), 떨어 뜨릴 때(EVENT_DROP_OBJECT) 이벤트가 발생한다.
  물체를 조합할 때(EVENT_COMBINE_OBJECT), 분해할 때(EVENT_DISMANTLE_OBJECT) 이벤트가 발생한다.
  KEYPAD 암호가 입력된 경우에 EVENT_KEYPAD 이벤트가 발생한다.

11. void [setMouseCallback](/api/bangtal_8h.html#a9b828a65e91609a44cd7e2ec8456e3b0)([MouseCallback](/api/bangtal_8h.html#a9612cf018b328681a31d38377b2cb3e5) callback)<br />
  물체에 마우스 입력을 수신하는 callback 함수를 설정한다.
  마우스를 클릭(MOUSE_CLICK)하거나 드래그(MOUSE_DRAG_UP/DONW/LEFT/RIGHT)가 발생한다.

12. void [setKeyboardCallback](/api/bangtal_8h.html#aead6d0852b832072d6c48d8d4c108565)([KeyboardCallback](/api/bangtal_8h.html#a6ba3385cbe76afca5db6ff18ae1bbd88) callback)<br />
  키보드 입력을 수신하는 callback 함수를 설정한다.
  키가 눌리는 경우에 코드와 상태(KEY_PRESSED / KEY_RELEASED)가 전달된다.

## 사운드(Sound) 관련 함수
1. [SoundID](/api/bangtal_8h.html#ac1b492d538b28c7f774773107f49c891) [createSound](/api/bangtal_8h.html#a0d0dd5b506199c1e936bc808ce84523f)(const char* sound)<br />
  사운드 파일(sound)로 사운드 객체를 생성하고 ID를 반환한다.
  ```c
  SoundID sound1 = createSound("Audios/Start.mp3");
  ```

2. void [playSound](/api/bangtal_8h.html#a0b0121f4e88b1abdb4ace47403db888e)([SoundID](/api/bangtal_8h.html#ac1b492d538b28c7f774773107f49c891) sound, bool loop = false) / void [stopSound](/api/bangtal_8h.html#a4c98327986f715b67c5c2552638f5df4)([SoundID](/api/bangtal_8h.html#ac1b492d538b28c7f774773107f49c891) sound)<br />
  사운드를 재생하고(playSound) 재생을 종료한다(stopSound).
  ```c
  playSound(sound1);
  ```

3. void [setSoundCallback](/api/bangtal_8h.html#a13a03dacd0c6849ae3f16d2e694fc280)([SoundCallback](/api/bangtal_8h.html#a53bae382c608281427e5c3cafd86b50c) callback)<br />
  사운드에서 발생하는 이벤트를 수신하는 callback 함수를 설정한다.
  사운드 재생이 종료될 때 이벤트(EVENT_SOUND)가 발생한다.

## 타이머(Timer) 관련 함수
1. [TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) [createTimer](/api/bangtal_8h.html#aff732779cd7227ae651b617ce6729ac7)([Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10) second = 0)<br />
  주어진 시간(second 초)으로 타이머 객체를 생성하고 ID를 반환한다.
  ```c
  TimerID timer1 = createTimer(10.5f);          // 10.5초
  ```

2. void [startTimer](/api/bangtal_8h.html#a2c710d58c45f43834f4fc7f362f70266)([TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) timer) / void [stopTimer](/api/bangtal_8h.html#a5677061589db77a1570d9a9f6a73988c)([TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) timer)<br />
  타이머를 시작하고(startTimer) 멈춘다(stopTimer)
  ```c
  startTimer(timer1);
  ```

3. [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10) [getTimer](/api/bangtal_8h.html#a73c8b044ab55f62cc5791e46d61fe930)([TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) timer)<br />
  타이머(timer)의 현재 시간(초)을 반환한다.

4. void [setTimer](/api/bangtal_8h.html#a65dc90fa00b1e4d61a3a521e48e5f7ed)([TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) timer, [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10) second) /
  void [increaseTimer](/api/bangtal_8h.html#aee25f08368d0dfc7491c48e2d61d5191)([TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) timer, [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10) second) / void [decreaseTimer](/api/bangtal_8h.html#a8796ad85a1ac86190555c7b4da112797)([TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) timer, [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10) second)<br />
  타이머(timer)의 현재 시간을 주어진 시간(second)으로 설정하거나(setTimer),
  주어진 시간 만큼 증가시키거나(increaseTimer) 감소시킨다(decreaseTimer).

5. void [showTimer](/api/bangtal_8h.html#a2c710d58c45f43834f4fc7f362f70266)([TimerID](/api/bangtal_8h.html#a46a79edf8de643e2431a15f55a193ee3) timer) / void [hideTimer](/api/bangtal_8h.html#a67ee81aa37d3b4804e61b57c61b03213)()<br />
  타이머(timer)를 보여주거나(showTImer) 숨긴다(hideTimer).

6. void [setTimerCallback](/api/bangtal_8h.html#a9ac3c89e07a2d4d3f9164ac6f14ea8cc)([TimerCallback](/api/bangtal_8h.html#a73a1311d525ad641bedca5d01369aa85) callback)<br />
  타이머에서 발생하는 이벤트를 수신하는 callback 함수를 설정한다.
  타이머가 종료될 때 이벤트(EVENT_TIMER)가 발생한다.

## 다이얼로그 관련 함수
1. void [showMessage](/api/bangtal_8h.html#aa3d14543ea624c7209e4cd2a9d33cb7a)(const char* message)<br />
  주어진 메시지(message)를 메시지 창에 보인다.

2. void [showImageViewer](/api/bangtal_8h.html#a47a52bcc4dd3b52f9a555e907e75901d)(const char* image)<br />
  주어진 이미지(image)를 보인다.

3. void [showKeypad](/api/bangtal_8h.html#aa4ddd7b05cd1b310ac133e0e7913718a)(const char* password, [ObjectID](/api/bangtal_8h.html#a9d43422939374d7485e494503ab30b8b) object)<br />
  주어진 암호(password)를 입력할 수 있는 키패드를 보인다.
  암호를 맞추면 이벤트(EVENT_KEYPAD)가 발생한다.
  ```c
  showKeypad("PASS1234", door1);
  ```
