---
title: "14주차 퀴즈"
permalink: /lectures/c++/quiz14/
---

## 문제1
다음 프로그램의 출력에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

void f3(int& n){
    if (n<5) throw n;
    cout << n << endl;
}

void f2(int& n){
    f3(++n);
    cout << n << endl;
}

void f1(int& n){
    try {
        f2(++n);
    }
    catch(int n){
        throw n+3;
    }
    cout << n << endl;
}

int main(){
    int n = 1;
    try {
        f1(++n);
    }
    catch(int n){
        cout << n << endl;
    }
    cout << n << endl;
}
```
