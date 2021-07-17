---
title: "3주차 퀴즈"
permalink: /lectures/c++/quiz03a/
---

## 문제1
다음 프로그램의 결과와<br />
각 변수에 저장된 값을 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    int n = 100;

    int *p1 = &n;
    int **p2 = &p1;

    printf("p1=%p, *p1=%d\n", p1, *p1);
    printf("p2=%p, *p2=%p, **p2=%d\n", p2, *p2, **p2);
}
```

## 문제2
다음 프로그램의 결과가 270이 아닌 이유를 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    int score[3] = { 80, 90, 100 };
    int sum = score[1] + score[2] + score[3];

    printf("sum = %d\n", sum);
}
```

## 문제3
"hello world"가 출력 될 수 있도록 다음 프로그램을 완성하세요(2점).

```c
#include <stdio.h>

int main()
{
    char buf[20];

    // insert your code

    printf("%s\n", buf);
}
```

## 문제4
입력된 두 문자열을 이어 붙이는 strcat() 함수를 완성하세요(2점).

```c
#include <stdio.h>

void strcat(const char* s1, const char* s2, char* s3) {
  // insert your code
}

int main() {
    char s1[10], s2[10], s3[20];

    scanf("%s %s", s1, s2);
    strcat(s1, s2, s3);
    printf("%s\n", s3);
}

```

## 문제5
메모리를 해제하는 delete 명령과 delete[] 명령의 차이를 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    int *pi = new int;
    *pi = 10;

    int *pj = new int[2];
    pj[0] = 20; pj[1] = 30;

    delete pi;
    delete pj;
}
```
