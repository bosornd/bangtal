---
title: "13주차 퀴즈"
permalink: /lectures/c/quiz13/
---

## 문제1
다음 프로그램에서 구조체의 크기가 다른 이유를 설명하세요(2점).

```c
#include <stdio.h>

int main()
{
    struct AAA {
        char ch1;
        int n;
        char ch2;
    };

    struct BBB {
        char ch1, ch2;
        int n;
    };

    printf("sizeof(AAA) = %ld\n", sizeof(AAA));
    printf("sizeof(BBB) = %ld\n", sizeof(BBB));
}
```

## 문제2
다음 프로그램의 출력으로 부동소수점(float)의 표현 방식에 대해서 설명하세요(4점).

```c
#include <stdio.h>

void print_float(float f) {
    union {
        unsigned int n;
        float f;
    } data;
    data.f = f;

    for(unsigned int m = 0x80000000; m; m >>= 1)
        printf("%d", (m & data.n) ? 1 : 0);
    printf("\n");
}

int main()
{
    print_float(2.f);
    print_float(1.f);
    print_float(.5f);
    print_float(.25f);
}
```

## 문제3
학생의 이름과 국어, 영어, 수학 점수를 포함하는 구조체(Student)를 생성하고,
구조제 배열에 학생들의 성적을 저장한다(학생의 수는 최대 30명이다).<br />
저장된 학생들의 성적으로부터 학생들의 평균과 표준편차를 출력하는 프로그램을
개발하고자 한다. 다음 프로그램을 완성하세요(4점).

```c
#include <stdio.h>
#include <math.h>

// 1. 이름과 국어/영어/수학 점수를 가지는 구조체를 생성하라.
struct Student
{
};

// 2. 학생의 이름, 국어/영어/수학 점수를 입력받는 함수를 작성하라.
void getData(struct Student* pStudent)
{
}

// 3. 학생의 이름, 국어/영어/수학 점수와 평균/표준편차를 출력하는 함수를 작성하라.
void printStudent(const struct Student* pStudent)
{
}

// 4. Student 배열을 선언하고,
//    배열에 학생 정보를 저장한다(getData() 함수 이용).
//    학생의 점수/평균/표준편차를 출력한다(printStudent() 함수 이용)
int main()
{
}
```

## 문제4
추가 설명이 필요한 것을 알려주세요.
