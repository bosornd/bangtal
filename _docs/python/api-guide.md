---
title: "API 가이드"
permalink: /docs/python/api-guide/
---

bangtal 모듈을 import 함으로써 Bangtal API를 사용할 수 있다.
```python
from bangtal import *
```

## 기본 함수
1. startGame(scene)<br />
   주어진 scene으로부터 게임을 시작한다.
   scene 객체의 생성 및 제어는 Scene 객체를 참고한다.
   게임이 시작되면 scene 객체의 onEnter callback이 호출된다.

2. endGame()<br />
   게임을 종료한다.

3. showTimer(timer)<br />
   timer 객체의 현재 시간을 화면에 보인다.
   timer 객체의 생성 및 제어는 Timer 객체를 참고한다.

4. hideTimer()<br />
   timer를 숨긴다.

5. showMessage(message)<br />
   메시지 창에 message를 보인다.

6. showImageViewer(image_file)<br />
   주어진 이미지 파일을 보인다.

7. showAudioPlayer(audio_file)<br />
   주어진 AUDIO 파일의 재생기를 보인다.

8. showVideoPlayer(video_file)<br />
   주어진 VIDEO 파일의 재생기를 보인다.

9. showKeypad(password, object)<br />
   암호를 입력할 수 있는 입력 창이 보인다.
   사용자가 주어진 암호(password)를 맞추는 경우에 object.onKeypad() 함수가 호출된다.<br />
   ex) showKeypad("PASS1234", door1)

## Scene 객체
1. 생성자 - Scene(name, image_file)<br />
   Scene 객체를 생성합니다.<br />
   ex) scene1 = Scene("룸1", "Images/배경-1.png")

2. setImage(image_file)<br />
   Scene 객체의 배경 이미지를 변경합니다.<br />
   ex) scene1.setImage("Images/배경-2.png")

3. setLight(light)<br />
   Scene 객체의 조명을 조절합니다. (0~1 사이의 값)<br />
   ex) scene1.setLight(0.7.     # 70%

4. enter()<br />
   scene으로 장면을 변경한다.
   이전 scene 객체의 onLeave callback이 호출되고
   장면이 변경된 다음에 scene 객체의 onEnter callback이 호출된다.

5. Scene에 들어오는 경우에 호출되는 callback 함수<br />
   a) onEnterDefault(scene): 모든 Scene 객체의 default callback 함수<br />
   b) onEnter(): 개별 Scene 객체의 callback 함수

6. Scene에서 나갈 경우에 호출되는 callback 함수<br />
   a) onLeaveDefault(scene): 모든 Scene 객체의 default callback 함수<br />
   b) onLeave(): 개별 Scene 객체의 callback 함수

7. Scene에서 key가 눌리는 경우에 호출되는 callback 함수<br />
   a) onKeyboardDefault(scene, key, pressed): 모든 Scene 객체의 default callback 함수<br />
   b) onKeyboard(key, pressed): 개별 Scene 객체의 callback 함수

## Object 객체
1. 생성자 - Object(image_file)<br />
   Object 객체를 생성합니다.<br />
   ex) door1 = Object("Images/문-오른쪽-닫힘.png")

2. setImage(image_file)<br />
   Object 객체의 이미지를 변경합니다.<br />
   ex) door1.setImage("Images/문-오른쪽-열림.png")

3. setScale(scale)<br />
   Object 객체의 크기를 조정합니다.<br />
   ex) door1.setScale(0.5.      # 50%

4. locate(scene, x, y)<br />
   Object 객체를 Scene에 위치시킵니다.<br />
   ex) door1.locate(scene1, 800, 270)

5. show() / hide()<br />
   Object 객체를 보이거나(show) 숨깁니다(hide).<br />
   ex) door1.show()

6. pick() / drop()<br />
   Object 객체를 줍거나(pick) 떨어뜨립니다(drop).<br />
   ex) key1.pick()

7. defineCombination(object1, object2)<br />
   Object 객체의 조합/분해하는 방법을 정의한다.
   Object 객체의 생성 및 제어는 Object 객체를 참고한다.
   object1과 object2를 조합(Combine)하면 현재 Object를 만들 수 있다.
   현재 Object를 분해(Dismantle)하면 object1과 object2를 얻을 수 있다.

8. inHand()<br />
   현재 사용중인 객체인가를 반환한다.

9. Object에 마우스 입력이 된 경우에 호출되는 callback 함수<br />
   a) onMouseActionDefault(object, x, y, action): 모든 Object 객체의 default callback 함수<br />
   b) onMouseAction(x, y, action): 개별 Object 객체의 callback 함수<br />
   action은 click과 drag가 있으며, MouseAction으로 정의되어 있다.<br />
   ```python
   if action==MouseAction.CLICK:
       print("Clicked")
   elif action==MouseAction.DRAG_RIGHT:
       print("Dragged to the Right")
   ```

10. Object를 줍거나 떨어 뜨릴 경우에 호출되는 callback 함수<br />
   a) onPickDefault(object): 모든 Object 객체의 default callback 함수<br />
      onDropDefault(object): 모든 Object 객체의 default callback 함수<br />
   b) onPick(): 개별 Object 객체의 callback 함수<br />
      onDrop(): 개별 Object 객체의 callback 함수

11. Object를 조합(Combine)하거나 분해(Dismantle)하는 경우에 호출되는 callback 함수<br />
   a) onCombineDefault(object): 모든 Object 객체의 default callback 함수<br />
      onDismantleDefault(object): 모든 Object 객체의 default callback 함수<br />
   b) onCombine(): 개별 Object 객체의 callback 함수<br />
      onDismantle(): 개별 Object 객체의 callback 함수

12. Keypad를 해결한 경우에 호출되는 callback 함수<br />
   a) onKeypadDefault(object): 모든 Object 객체의 default callback 함수<br />
   b) onKeypad(): 개별 Object 객체의 callback 함수

## Sound 객체
1. 생성자 - Sound(sound_file)<br />
   Sound 객체를 생성합니다.<br />
   ex) sound1 = Sound("Audios/Start.mp3")

2. play(loop = False) / stop()<br />
   Sound 객체를 재생(play)하거나 종료(stop)합니다.<br />
   ex) sound1.play(True)

3. 재생이 종료된 경우에 호출되는 callback 함수<br />
   a) onCompletedDefault(object): 모든 Sound 객체의 default callback 함수<br />
   b) onCompleted(): 개별 Sound 객체의 callback 함수

## Timer 객체
1. 생성자 - Timer(seconds)<br />
   Timer 객체를 생성합니다.<br />
   ex) timer1 = Timer(10.5)       # 10.5초

2. start() / stop()<br />
   Timer 객체를 시작(start)하거나 종료(stop)합니다.<br />
   ex) timer1.start()

3. get()<br />
   Timer 객체의 현재 시간을 반환합니다.

4. set(seconds), increase(seconds), decrease(seconds)<br />
   Timer 객체의 현재 시간을 설정(set), 증가(increase), 감소(decrease)시킵니다.

5. 시간이 지난 경우에 호출되는 callback 함수<br />
   a) onTimeoutDefault(object): 모든 Timer 객체의 default callback 함수<br />
   b) onTimeout(): 개별 Timer 객체의 callback 함수
