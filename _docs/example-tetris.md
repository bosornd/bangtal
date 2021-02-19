---
title: "예제: 테트리스"
permalink: /docs/example-tetris/
excerpt: "테트리스"
modified: "2021-02-19 13:51:00 +0900"
---
Developed by 이원형
- [https://github.com/bosornd/Tetris](https://github.com/bosornd/Tetris)
- [https://github.com/0224wonhyoung/Tetris](https://github.com/0224wonhyoung/Tetris)

## 게임 소개

<figure>
  <img src="https://user-images.githubusercontent.com/63161899/96385307-0208d300-11ce-11eb-902c-6b349ae60143.png">
</figure>

반복해서 나오는 4개의 사각형을 조합한 테트로미노 7종류를 쌓는 게임입니다.

<figure>
  <img src="https://user-images.githubusercontent.com/63161899/96385248-a2aac300-11cd-11eb-8b3f-603168da9168.PNG">
</figure>

맨 위에서 나와 주기적으로 밑으로 낙하하는 블록이 현재블록입니다.  
그 밑에 회색 블록은 현재 블록이 떨어지는 예상 위치이고, 게임판 좌우에 각각 보관함(HOLD)와 다음번블록(NEXT)가 있습니다.

<figure>
  <img src="https://user-images.githubusercontent.com/63161899/96385246-a2aac300-11cd-11eb-91a5-9358919179f4.PNG">
</figure>

현재 블록은 시계/반시계 방향으로 돌리거나, 한칸 옆으로 움직이거나(위로 다시 올릴수는 없습니다.), 제일 아래로 내릴 수 있습니다.  
블록이 완전히 낙하하게되면 다음 블록이 나오고, 그 전에 저장해놓은 블록과 현재블록을 맞바꿀 수 있습니다.

---

블록을 각각의 줄이 꽉 차도록 채우는게 목표입니다.  
줄을 블록으로 꽉 채우면 그 줄이 사라지고 위에있던 블록들이 내려옵니다.
<figure>
  <img src="https://user-images.githubusercontent.com/63161899/96385243-a1799600-11cd-11eb-91ec-3fd99601ec29.PNG">
</figure>
<figure>
  <img src="https://user-images.githubusercontent.com/63161899/96385244-a1799600-11cd-11eb-8384-4d1063f571a6.PNG">
</figure>
<figure>
  <img src="https://user-images.githubusercontent.com/63161899/96385245-a2122c80-11cd-11eb-9382-0fc3953f3433.PNG">
</figure>

줄을 꽉 채우면 보스에게 데미지를 줄 수 있습니다.  
데미지는 한번에 많은 줄을 지울수록, 연속해서 줄을 지워 콤보를 쌓을수록 높아집니다.  
1줄 = 100  
2줄 = 200  
3줄 = 400  
4줄 = 600  
데미지 = 기본데미지 * (1 + 0.1*콤보) (단, 최대 콤보는 5)  
블록을 잘 쌓아 자쿰의 체력 5000을 깎아 무찌르세요.
