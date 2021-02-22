---
title: "5주차 퀴즈"
permalink: /lectures/c/quiz05/
---

## 문제1
다음 프로그램의 출력은(1점)?<br />
변수 a가 저장하는 값은 문자('c')인데, 출력이 'c'가 아닌 이유를 설명하세요(1점).

```c
#include <stdio.h>

int main()
{
    char a = 'c';
    printf("%d", a);
}
```

## 문제2
다음 프로그램의 출력은(1점)?<br />
출력의 결과로 음수 표현에 대해서 설명하세요(1점).

```c
#include <stdio.h>

int main()
{
    int x;
    scanf("%d", &x);

    int y = ~x + 1;
    printf("%d", x + y);
}
```

## 문제3
다음 프로그램의 출력은(1점)?<br />
출력 결과로 시프트 연산(<<, >>)과 곱셈/나눗셈에 대해서 설명하세요(1점).

```c
#include <stdio.h>

int main()
{
    int x, y;
    scanf("%d", &x);

    y = x << 5;
    y += x << 3;
    y += x;

    printf("%d\n", y / x);
}
```

## 문제4
다음 프로그램의 출력은(1점)?<br />
출력 결과에 대해서 설명하세요(1점).

```c
#include <stdio.h>

int main()
{
    for(int i = 0, n = 1; i < 32; ++i, n *= 2)
        printf("%d\n", n);
}
```

## 문제5
다음 프로그램의 출력은(1점)?<br />
출력 결과에 대해서 설명하세요(1점).

```c
#include <stdio.h>

int main()
{
    int x = 55;
    float y1 = 1. / x;
    float y2 = y1 * x;
    int z = y2;
    bool b1 = (y2 == 1);
    bool b2 = (y2 == 1.);

    printf("%d %f %f %d %d %d\n", x, y1, y2, z, b1, b2);
}
```

## 문제6
추가 설명이 필요한 것을 알려주세요.
