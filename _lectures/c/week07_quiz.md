---
title: "7주차 퀴즈"
permalink: /lectures/c/quiz07/
---

## 문제1
반복문 for와 while의 표현 범위가 동일함을 증명하세요(2점).

## 문제2
다음 프로그램의 출력은(1점)?<br />
n을 수식으로 나타내면 어떻게 될까요(1점)?

```c
#include <stdio.h>

int main()
{
    int n = 0, d = 1;	             // line 5
    for ( ; ; d <<= 1 ){	     // line 6
        if ( n > 10 ) break;	     // line 7
        if ( d % 10 > 5 ) continue;  // line 8
        n += d;		             // line 9
    }
    printf("%d", n);	             // line 11
}
```

## 문제3
*를 이용해서 다이아몬드 모양을 출력하는 함수 print_diamond()를 완성하세요(3점).

- n이 1인 경우
```
*
```
- n이 2인 경우
```
 *
***
 *
```
이런 식으로 출력됩니다.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

void print_diamond(unsigned n) {
    // insert your code here
}

int main() {
    unsigned n;
    scanf("%d", &n);
    print_diamond(n);
}
```

## 문제4
각 변의 길이가 100보다 작은 자연수 일 때, 직각 삼각형이 되는 경우의 수를 구하는 프로그램을 작성하세요(3점).


## 문제5
추가 설명이 필요한 것을 알려주세요.
