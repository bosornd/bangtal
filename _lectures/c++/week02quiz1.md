---
title: "2주차 퀴즈"
permalink: /lectures/c++/quiz02a/
---

## 문제1
다음 프로그램의 출력과<br />
음수 표현 방법에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    int x, y;
    scanf("%d", &x);

    y = ~x;
    printf("%d\n", x + y);
}
```

## 문제2
다음 프로그램의 출력에 대해서 설명하세요(2점).

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

## 문제3
다음 프로그램의 출력에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    char ch1 = 0x7F;
    char ch2 = ch1 + 1;
    int    n = ch1 + 1;
    printf("%d, %d\n", ch2, n);

    int  n1 = 0x7FFFFFFF;
    int  n2 = n1 + 1;
    long ll = n1 + 1;
    printf("%d, %ld\n", n2, ll);
}
```

## 문제4
다음 프로그램의 출력에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    unsigned int n;
    scanf("%u", &n);

    switch(n % 5){
        case 1: n++;
        case 2: n++;
        case 3: n++;
        case 4: n++;
    }

    printf("%d", n % 5);
}
```

## 문제5
입력한 정수형 데이터의<br />
이진수 표현을 출력하는 프로그램을 작성하세요(2점).<br />
예) 입력: 10, 출력: 00000000000000000000000000001010
