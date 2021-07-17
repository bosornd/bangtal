---
title: "4주차 퀴즈"
permalink: /lectures/c++/quiz04a/
---

## 문제1
다음 프로그램에서 두 구조체의 크기가 다른 이유를 설명하세요(2점).

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
학생의 이름과 국어, 영어, 수학 점수를 포함하는 구조체(Student)를 생성하고,
구조체 배열에 학생들의 성적을 저장한다(학생의 수는 최대 30명이다).<br />
저장된 학생들의 성적으로부터 학생들의 평균과 표준편차를 출력하는 프로그램을
개발하고자 한다. 다음 프로그램을 완성하세요(8점).

```c
#include <stdio.h>

// 1. 이름과 국어/영어/수학 점수를 가지는 구조체를 생성하라.
struct Student {
};

// 2. 학생의 이름, 국어/영어/수학 점수를 입력받는 함수를 작성하라.
void getData(struct Student* pStudent) {
}

// 3. 학생의 이름, 국어/영어/수학 점수와 평균/표준편차를 출력하는 함수를 작성하라.
void printStudent(const struct Student* pStudent) {
}

// 4. Student 배열을 선언하고,
//    배열에 학생 정보를 저장한다(getData() 함수 사용)
//    학생의 점수/평균/표준편차를 출력한다(printStudent() 함수 사용)
int main()
{
}
```
