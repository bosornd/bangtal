---
title: "10주차 퀴즈"
permalink: /lectures/c/quiz10/
---

## 문제1
다음은 [피보나치 수열](https://en.wikipedia.org/wiki/Fibonacci_number)의 정의입니다.<br />
<img src="/assets/images/fibonacci.png" alt="Fibonacci Sequence"><br />
이를 구현하는 재귀 함수 fibonacci()를 완성하세요(2점).

```c
#include <stdio.h>

unsigned long long fibonacci(unsigned int n)
{
    // insert code here
}

int main()
{
    unsigned int n;
    scanf("%u", &n);
    printf("fibonacci(%u) = %llu", n, fibonacci(n));
}
```

## 문제2
상기 재귀 함수로 fibonacci(70)을 구해보자.<br />
실행하면 묵묵부답. 아무리 기다려도 답이 나오지 않는다.<br />
얼마나 오래 걸릴까? 예상 시간은(1점)?

## 문제3
재귀 함수를 사용하지 않고,<br />fibonacci(70)을 구하는 프로그램을 작성하라(2점).

## 문제4
종을 칠 때마다 암탉은 알을 낳고, 알은 병아리가, 병아리는 암탉이 된다고 하자.
처음에 한 마리 암탉만 있을 때, 종을 N(<100)번 치면 암탉, 병아리, 알의 수가
얼마나 되는 지를 출력하는 프로그램을 작성하라(5점).

예를 들어, N이 1이면, 암탉 1마리, 알 1개가 된다.<br />
N이 2이면, 암탉 1마리, 병아리 1마리, 알 1개가 된다.<br />
N이 3이면 암탉 2마리, 병아리 1마리, 알 1개가 된다.<br />
N이 4이면 암탉 3마리, 병아리 1마리, 알 2개가 된다.

## 문제5
추가 설명이 필요한 것을 알려주세요.
