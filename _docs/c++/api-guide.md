---
title: "API 가이드"
permalink: /docs/c++/api-guide/
---

다음 문장을 포함함으로써 [Bangtal API](/api/namespacebangtal.html)를 사용할 수 있다.
```c++
#include <bangtal>
```

C++ bangtal library는 bangtal namespace로 정의되어 있으므로 bangtal namespace를
사용하도록 선언하는 것이 좋다.
```c++
using namespace bangtal;
```

## 기본 함수

1. void [startGame](/api/namespacebangtal.html#a8eb706a2a0ed55817c95ef990086d99b)([ScenePtr](/api/namespacebangtal.html#abb35c3c750f71093eb016b9d812066e3) scene)<br />
  scene으로부터 게임을 시작한다.
  scene으로 들어가면서 이벤트(EVENT_ENTER_SCENE)가 발생한다.

2. void [endGame](/api/bangtal_8h.html#aeda119595fcc834db9cfec532a90cf79)()<br />
  게임을 종료한다.

3. void [showTimer](/api/namespacebangtal.html#a3532e67e12de8b00991f500e5af97bf3)([TimerPtr](/api/namespacebangtal.html#ad66ed2b2b36b443dfc7e8987cdfaf0d8) timer)<br />
  주어진 타이머를 게임 화면에 보인다.

4. void [hideTimer](/api/bangtal_8h.html#a67ee81aa37d3b4804e61b57c61b03213)()<br />
  타이머를 보이지 않는다.

5. void [showMessage](/api/namespacebangtal.html#a97a439a0bf46cf493cfeaa9e03f7fd2b)(const std::string& message)<br />
  주어진 메시지(message)를 메시지 창에 보인다.

6. void [showImageViewer](/api/namespacebangtal.html#aa883eb18b1eb1c035ffd844e6d321350)(const std::string& image)<br />
  주어진 이미지(image)를 보인다.

7. void [showKeypad](/api/namespacebangtal.html#a9c5b0d72a37bf89ce507dca1c8a049b6)(const std::string& password, [ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59) object)<br />
  주어진 암호(password)를 입력할 수 있는 키패드를 보인다.
  암호를 맞추면 이벤트(EVENT_KEYPAD)가 발생한다.
  ```c++
  showKeypad("PASS1234", door1);
  ```
​

## 장면(Scene) 클래스

1. static [ScenePtr](/api/namespacebangtal.html#abb35c3c750f71093eb016b9d812066e3) [create](/api/classbangtal_1_1_scene.html#a3ad3e0db50cac0a549f7342e28d33f7c)(const std::string& name, const std::string& image)<br />
  주어진 이름(name)과 배경 이미지(image)를 가진 장면을 생성하고 [ScenePtr](/api/namespacebangtal.html#abb35c3c750f71093eb016b9d812066e3)를 반환한다.
  ```c++
  ScenePtr scene = Scene::create("룸1", "Images/배경-1.png");
  ```

2. void [setImage](/api/classbangtal_1_1_scene.html#aabbdbbc029198ca7a15059d90823efff)(const std::string& image)<br />
  장면(scene)의 배경 이미지(image)를 변경한다.
  ```c++
  scene->setImage("Images/배경-2.png");
  ```

3. void [setLight](/api/classbangtal_1_1_scene.html#ad6ecb6f139a50a3a2d2ae839078f9481)([SceneLight](/api/bangtal_8h.html#ac1f211f483e9d9c2ec4c8ae0d98f6977) light)<br />
  장면(scene)의 밝기(light)를 조정한다. light는 0~1 사이의 float 값이다.
  ```c++
  scene->setLight(0.5f);      // 50%
  ```

4. void [enter](/api/classbangtal_1_1_scene.html#a42699aaea50be2e6069b87144a1d066c)()<br />
  장면(scene)으로 이동한다.
  현재 장면에서 EVENT_LEAVE_SCENE이 발생하며,
  이동한 장면에서 EVENT_ENTER_SCENE이 발생한다.
  ```c++
  scene->enter();
  ```

6. 장면에서 들어오는 경우에 처리하는 Event Handler - bool [onEnter](/api/classbangtal_1_1_scene.html#aab3b03a899b70725e5093bb3b7498e3e)()<br />
  기본적으로 onEnterCallback 함수를 호출한다.
  [setOnEnterCallback](/api/classbangtal_1_1_scene.html#af2cd661c238a4155ba4de48856302fa1)() 함수를 통해서 재정의 할 수 있다.
  ```c++
  scene->setOnEnterCallback([](ScenePtr scene)->bool {
           std::cout << "entering into " << scene->getName() << std:endl;
       });
  ```

6. 장면에서 나가는 경우에 처리하는 Event Handler - bool [onLeave](/api/classbangtal_1_1_scene.html#a4bda78a3352a7eac3f2da3bb93c3a3e8)()<br />
  기본적으로 onLeaveCallback 함수를 호출한다.
  [setOnLeaveCallback](/api/classbangtal_1_1_scene.html#a26ebf99350dd830e21d7780c7b9f7108)() 함수를 통해서 재정의 할 수 있다.
  ```c++
  scene->setOnLeaveCallback([](ScenePtr scene)->bool {
           std::cout << "leaving from " << scene->getName() << std:endl;
       });
  ```

7. 키보드 입력을 처리하는 Event Handler - bool [onKeyboard](/api/classbangtal_1_1_scene.html#abde24596b74c68d180596fd93d3e9236)([KeyCode](/api/bangtal_8h.html#a94b769a2899b14202ace87b550519a0d) key, bool pressed)<br />
  기본적으로 onKeyboardCallback 함수를 호출한다.
  [setOnKeyboardCallback](/api/classbangtal_1_1_scene.html#a3b96d28deda5de26da1c724c65b9227d)() 함수를 통해서 재정의 할 수 있다.
  ```c++
  scene->setOnKeyboardCallback([](ScenePtr scene, KeyCode key, bool pressed)->bool {
           std::cout << key << (pressed ? " pressed" : " released") << std:endl;
       });
  ```

## 물체(Object) 클래스

1. static [ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59) [create](/api/classbangtal_1_1_object.html#a8acd0706b38dce38fe14971bca3d2b5f)(const std::string& image, [ScenePtr](/api/namespacebangtal.html#abb35c3c750f71093eb016b9d812066e3) scene, int x, int y, bool shown)<br />
  주어진 이미지(image)로 물체를 생성하고 [ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59)를 반환한다.
  물체를 주어진 장면(scene)의 (x, y)에 위치시킨다.
  물체를 보이도록 설정한다(shown).
  ```c++
  ObjectPtr door = Object::create("문1", "Images/문-오른쪽-닫힘.png", scene1, 800, 270, true);
  ```

2. void [setImage](/api/classbangtal_1_1_object.html#a9bf28ee253ffaaad4bb25e9beb80c70b)(const std::string& image)<br />
  물체(object)의 이미지(image)를 변경한다.
  ```c++
  door->setImage("Images/문-오른쪽-열림.png");
  ```

3. void setText(const std::string& text)<br />
  물체(object)의 텍스트(text)를 변경한다.
  ```c++
  door->setText("한글 ABC\n123456");
  ```


4. void [setScale](/api/classbangtal_1_1_object.html#aeb5f1aba5c856072368001103f78711e)([ObjectScale](/api/bangtal_8h.html#a537d96924958a57df4f79361694478d1) scale)<br />
  물체(object)의 크기(scale)를 조정한다. 1이 100%이며 float 값이다.
  ```c++
  door->setScale(0.5f);      // 50%
  ```

5. void [locate](/api/classbangtal_1_1_object.html#ae5542aabd52dc1d64c71a24bc2f4ff59)([ScenePtr](/api/namespacebangtal.html#abb35c3c750f71093eb016b9d812066e3) scene, int x, int y)<br />
  물체(object)를 장면(scene)의 (x, y)로 위치시킨다.
  ```c++
  door->locate(scene1, 900, 270)
  ```

6. void [show](/api/classbangtal_1_1_object.html#a3f2cb2a14439a9a74aaf6bd5bf5b8c16)() / [hide](/api/classbangtal_1_1_object.html#a2df4da449414f69a6ecfc79027412d22)()<br />
  물체(object)를 보이거나(show) 숨깁니다(hide).
  ```c++
  key->show()
  ```

7. void [pick](/api/classbangtal_1_1_object.html#a2b7d74354b53fff7a8ef913b2e1eb020)() / [drop](/api/classbangtal_1_1_object.html#af77fae71ec4bc0492a97d1a388bada3c)()<br />
  물체(object)를 줍거나(pick) 떨어뜨립니다(drop).
  ```c++
  key->pick()
  ```

8. void [defineCombination](/api/classbangtal_1_1_object.html#a1b0c8562232a1532bfa13468780b3849)([ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59) obj1, [ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59) obj2)<br />
  2개의 물체 obj1과 obj2를 조합(combine)하면 물체(object)를 생성할 수 있습니다.
  반대로 물체(object)를 분해(dismantle)하면 2개의 물체 obj1과 obj2를 얻을 수 있습니다.

9. bool [isHanded](/api/classbangtal_1_1_object.html#ae1776922c90a3fc51d4b70d0e4d8ce2a)()<br />
  물체(object)가 사용 중인가를 반환합니다.
  ```c++
  key->isHanded()
  ```

10. 물체(object)의 마우스 입력을 처리하는 Event Handler - bool [onMouse](/api/classbangtal_1_1_object.html#ab4780f0765cce0a58d816a9ada7424a3)(int x, int y, [MouseAction](/api/bangtal_8h.html#ac238b2b97468572bf2da46b80a3b1bb3) action)<br />
  기본적으로 onMouseCallback 함수를 호출한다.
  [setOnMouseCallback](/api/classbangtal_1_1_object.html#a819900bf45f0829982cd2ab9de307641)() 함수를 통해서 재정의 할 수 있다.
  ```c++
  door->setOnMouseCallback([]([ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59) object, int x, int y, MouseAction action)->bool {
           object->setImage("Images/문-오른쪽-열림.png");
       });
  ```
​
11. 물체(object)를 줍거나 떨어뜨리는 이벤트를 처리하는 Event Handler - bool [onPick](/api/classbangtal_1_1_object.html#ae0ae0c5cc37a5c932c2e258c11c08757)() / [onDrop](/api/classbangtal_1_1_object.html#afec5fb2c1014656489dd097b5e31b7b0)()<br />
  기본적으로 onPickCallback 함수를 호출한다.
  [setOnPickCallback](/api/classbangtal_1_1_object.html#a0d38b6dd0f563bc10fda594fd125dc8a)() 함수를 통해서 재정의 할 수 있다.
  ```c++
  paper->setOnPickCallback([]([ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59) object)->bool {
           object->setImage("Images/문서.png");
       });
  ```

12. 물체(object)를 조합/분해하는 이벤트를 처리하는 Event Handler - bool [onCombine](/api/classbangtal_1_1_object.html#a855c9c073bd14f961c51a5c13a489b8b)() / [onDismantle](/api/classbangtal_1_1_object.html#adc5a0564ea093c0aec1fadc3ddc1522c)()<br />
  기본적으로 onCombineCallback 함수를 호출한다.
  [setOnCombineCallback](/api/classbangtal_1_1_object.html#a563b0eb0030c0a843e1053cfd61e9c85)() 함수를 통해서 재정의 할 수 있다.

13. 키패드(keypad)를 완성하는 이벤트를 처리하는 Event Handler - bool [onKeypad](/api/classbangtal_1_1_object.html#aea58f22f73316a106fb7d0c911509563)()<br />
  기본적으로 onKeypadCallback 함수를 호출한다.
  [setOnKeypadCallback](/api/classbangtal_1_1_object.html#a57f2ca3027ce3deb9079fa748440ef8c)() 함수를 통해서 재정의 할 수 있다.
  ```c++
  door->setOnKeypadCallback([&]([ObjectPtr](/api/namespacebangtal.html#a58bcfbb10dc18b44fb41c19c4d850a59) object)->bool {
           showMessage("철커덕 문이 열렸다");
           door_unlocked = true;
       });
  ```

## 사운드(Sound) 클래스

1. static [SoundPtr](/api/namespacebangtal.html#a8d3868b6dff966e69e1bb0d6f1ee5e40) [create](/api/classbangtal_1_1_sound.html#aafcd3308ff1e33f7695cfdc9651c6f85)(const std::string& audio)<br />
  주어진 오디오 파일(audio)로 사운드 객체를 생성하고 [SoundPtr](/api/namespacebangtal.html#a8d3868b6dff966e69e1bb0d6f1ee5e40)를 반환한다.
  ```c++
  SoundPtr sound = Sound::create("Sounds/Start.mp3");
  ```

2. void [play](/api/classbangtal_1_1_sound.html#a0df5886045f4faeea33ddd55709f3b57)(bool loop = false) / [stop](/api/classbangtal_1_1_sound.html#a45589968fdfa9a2fdabf4e95c0170295)()<br />
  사운드(sound)를 재생(play)하거나 종료(stop)한다.
  ```c++
  sound->play(true);
  ```

3. 사운드(sound) 재생 종료 이벤트를 처리하는 Event Handler - bool [onSound](/api/classbangtal_1_1_sound.html#a4138876d4718c06af3d181f549e58ab5)()<br />
  기본적으로 onSoundCallback 함수를 호출한다.
  [setOnSoundCallback](/api/classbangtal_1_1_sound.html#ab6a1524d529e68762a7ef9422148a983)() 함수를 통해서 재정의 할 수 있다.

## 타이머(Timer) 클래스

1. static [TimerPtr](/api/namespacebangtal.html#ad66ed2b2b36b443dfc7e8987cdfaf0d8) [create](/api/classbangtal_1_1_timer.html#a2e682cbfc0a47c3f1cc756019a31ea90)(const [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10)& second)<br />
  주어진 시간(second)으로 타이머 객체를 생성하고 [TimerPtr](/api/namespacebangtal.html#ad66ed2b2b36b443dfc7e8987cdfaf0d8)를 반환한다.
  ```c++
  TimerPtr timer = Timer::create(10.f);
  ```
​
2. void [start](/api/classbangtal_1_1_timer.html#aa8b9803645d8a7c7d933d534e83315fd)() / [stop](/api/classbangtal_1_1_timer.html#ab56865402607dce713b363d9ff84a594)()<br />
  타이머(timer)를 시작(start)하거나 종료(stop)한다.
  ```c++
  timer->start()
  ```

3. void [set](/api/classbangtal_1_1_timer.html#add4f73ddfb3f08f27dfbf2bacde151f5)(const [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10)& second) / [increase](/api/classbangtal_1_1_timer.html#a6f282f1b8022410ef2c2913391975f76)(const [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10)& second) / [decrease](/api/classbangtal_1_1_timer.html#ad384d3ee4705269b5ddf19134289d77f)(const [Second](/api/bangtal_8h.html#a5c08c0353fd36f12c1b2ef409eb6db10)& second)<br />
  타이머(timer)를 설정(set)하거나 증가(increase), 또는 감소(decrease)시킨다.
  ```c++
  timer->set(10.f)
  ```

4. 타이머(timer) 종료 이벤트를 처리하는 Event Handler - bool [onTimer](/api/classbangtal_1_1_timer.html#af6aa65e756543e0da8c190ee39ee75d7)()<br />
  기본적으로 onTimerCallback 함수를 호출한다.
  [setOnTimerCallback](/api/classbangtal_1_1_timer.html#aa536afbba1b2f3c7e706e71afc9928a8)() 함수를 통해서 재정의 할 수 있다.
