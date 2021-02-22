---
title: "6주차 퀴즈"
permalink: /lectures/c/quiz06/
---

## 문제1
다음 프로그램의 출력은(1점)?<br />
출력에 대해서 설명하세요(1점).

```c
#include <stdio.h>

int main() {
    int a = 0, b = 0;

    if ( a = b ){
        printf("Same!!!\n");
    }
    else {
        printf("Different!!!\n");
    }
}
```

## 문제2
다음 프로그램의 출력은(1점)?<br />
출력에 대해서 설명하세요(1점).

```c
#include <stdio.h>

int main() {
    int a = 1, b = 1;

    if (a++ < 2 && a++ < 3 && a++ < 4)
        printf("%d\n", a);

    if (b++ < 2 || b++ < 3 || b++ < 4)
        printf("%d\n", b);
}
```

## 문제3
다음 프로그램의 출력은(1점)?<br />
출력에 대해서 설명하세요(1점).

```c
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>

int main() {
    int x;
    scanf("%d", &x);

    switch (x % 5) {
        case 1: x++;
        case 2: x++;
        case 3: x++;
        case 4: x++;
    }
    printf("%d", x % 5);
}
```

## 문제4
다음 프로그램은 가위/바위/보 게임 프로그램입니다.<br />
입력된 A, B 값으로부터 누가 이겼는지를 출력합니다.<br />
다음 프로그램을 완성하세요(4점).

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

#define ROCK        0
#define PAPER       1
#define SCISSORS    2

// insert your code here

int main() {
    unsigned A, B;
    scanf("%d %d", &A, &B);

    if ( A < 3 && B < 3){
        switch(winner(A, B)){
            case 1  : printf("A wins.\n"); break;
            case -1 : printf("B wins.\n"); break;
            default : printf("Game drew.\n"); break;
        }
    }
}
```

## 문제5
추가 설명이 필요한 것을 알려주세요.
