---
title: "11주차 퀴즈"
permalink: /lectures/c/quiz11/
---

## 문제1
다음 프로그램의 출력 결과에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    int a = 1, b = 2, c = 3;
    int* p = &b;

    printf("%d %d\n", &a-&b, &b-&c);
    printf("%d %d %d", *p, *(p+1), *(p-1));
}
```

## 문제2
다음 프로그램의 출력 결과와 연산자 우선순위에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    int a = 1, b = 2, c = 3;
    int* p = &b;

    printf("%d %d\n", &a-&b, &b-&c);
    printf("%d ", *p++);
    printf("%d ", (*p)--);
    printf("%d ", *p);
}
```

## 문제3
다음 프로그램의 출력 결과에 대해서 설명하세요(2점).

```c
#include <stdio.h>

void f(int* p){
    static int data = 5;
    p = &data;
}

int main()
{
    int* p = NULL;
    f(p);
    printf("%d", *p);
}
```

## 문제4
다음 프로그램의 출력 결과에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int* p = NULL;
void f(){
    int n = 1;
    p = &n;
}

void g(){
    int n = 2;
    n = n + 1;
}

int main()
{
    f(); g();
    printf("%d\n", *p);
}
```

## 문제5
N명(최대 30)의 국어, 영어, 수학 점수를 입력 받아서<br />다음을 출력하는 프로그램을 작성하세요(4점).<br />
- 각 과목의 최소, 최대, 평균<br />
- 각 학생 평균 점수의 최소, 최대, 평균

점수는 0부터 100까지 자연수이며<br />평균값은 소수점 2자리까지 출력할 것.

## 문제6
추가 설명이 필요한 것을 알려주세요.
