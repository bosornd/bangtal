---
title: "[문제] 로마 숫자 계산기"
permalink: /posts/roman-calculator/
date: "2023-02-05 09:14:25 +0900"
categories:
  - programming
---
주어진 로마 숫자 계산식의 결과를 출력하는 프로그램을 작성하라.

## 문제
<figure>
  <a href="/public/roman_table.png">
  <img src="/public/roman_table.png" alt="로마 숫자 테이블"></a>
</figure>
1. 로마숫자는 다음 7개 기호로 표현된다. 단, 0을 표현하기 위해서 Z를 추가한다.
2. 연산자 우선순위는 무시한다.
```
II + II * II = VIII
```
3. 상기 표현 방법에 맞지 않는 로마숫자가 포함된 경우에는 연산을 초기화 한다.
```
I + IIII + I = I
```
4. 연산 결과가 상기 표현 방법으로 표현할 수 없는 경우에도 연산을 초기화 한다.
```
I + C * C + I = I
```
5. 로마숫자와 연산자 사이에는 공백 문자가 포함될 수 있다.

## 테스트

1. 다음 테스트 파일의 모든 테스트 케이스에 성공하면 완성이다.<BR>
[테스트 파일: RomanCalc_TC.txt](/public/RomanCalc_TC.txt)
2. 테스트 파일은 다음과 같이 구성된다.
- 첫번째 줄에 테스트 케이스 개수가 있다.
- 각각의 테스트 케이스는 1라인에 작성된다.
- 테스트 케이스는 로마 숫자 계산식 = 결과로 구성되어 있다.
- 로마 숫자 계산식으로 계산하고 결과로 확인한다.
```
3
II + II * II = VIII
I + IIII + I = I
I + C * C + I = I
```
