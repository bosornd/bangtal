---
title: "12주차 퀴즈"
permalink: /lectures/c/quiz12/
---

## 문제1
다음 프로그램의 출력 결과에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    int a[3] = { 1, 2 };
    int *p = a;

    printf("%ld\n", sizeof(a));
    printf("%ld\n", sizeof(a + 1));
    printf("%ld\n", sizeof(a[0]));

    printf("%ld\n", sizeof(p));
    printf("%ld\n", sizeof(*p));
}
```

## 문제2
다음 프로그램의 출력 결과에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    char s[4] = { 'a', 'b', 'c', 'd' };
    printf("%c%c%c%c\n", s[0], s[1], s[2], s[3]);
    printf("%s\n", s);
}
```

## 문제3
다음 프로그램의 문제점에 대해서 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    char s[4] = "abcd";
    printf("%s\n", s);
}
```

## 문제4
입력된 두 문자열을 이어 붙이는 strcat() 함수를 완성하세요(2점).

```c
#include <stdio.h>

// s3 = s1 + s2, s3에 s1과 s2를 이어 붙인다.
void strcat(char* s1, char* s2, char* s3)
{
    // insert code here
}

int main()
{
    char s1[10], s2[10], s3[20];

    scanf("%s %s", s1, s2);
    strcat(s1, s2, s3);
    printf("%s\n", s3);
}
```

## 문제5
첫번째 문자열(str1)에서 두번째 문자열(str2)이 처음 나타나는 위치를 반환하는 함수 strstr() 함수를 완성하세요. 예를 들어, str1 = "Tom likes to eat Jerry"이고, str2 = "like"이면 str1+4가 반환된다. 나타나지 않으면 NULL을 반환한다.

```c
#include <stdio.h>

// str1에서 str2가 나타나는 위치를 반환한다.
char* strstr(char* str1, char* str2)
{
    // insert code here
}

int main()
{
    char s1[100], s2[100];

    scanf("%s %s", s1, s2);
    char* s3 = strstr(s1, s2);
    printf("%s\n", s3);
}
```

## 문제6
추가 설명이 필요한 것을 알려주세요.
