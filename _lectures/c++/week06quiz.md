---
title: "6주차 퀴즈"
permalink: /lectures/c++/quiz06/
---

## 문제1
다음 프로그램의 출력과 생성자/소멸자의 호출에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

class S {
    string name;

public:
    S(const string &n = "") : name(n) {
        cout << "CREATE: " << name << endl;
    };
    ~S(){
        cout << "DESTROY: " << name << endl;
    };

} gs("gs");

int main() {
    S tom("tom"), jane("jane");

    cout << "MAIN" << endl;
}
```

## 문제2
다음 프로그램의 출력에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

struct A {
    A(int n = 0){ cout << "A" << n << endl; };
} ga;

struct B {
    A a1, a2;
    B(int n = 0) : a1(n--), a2(n--){ cout << "B" << n << endl; };
};

int main() {
    B b1, b2(2);
}
```

## 문제3
다음 프로그램의 결과와 복사 생성자에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

class S {
    string name;

public:
    S(const string &n = "") : name(n) {
        cout << name << endl;
    };
    S(const S &c) : name(c.name + "_copy") {
        cout << name << endl;
    };
};

int main()
{
    S tom("tom");
    S tom2(tom), tom3 = tom2;
}
```

## 문제4
다음 프로그램의 출력과 생성자의 호출에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

struct A {
    int n;
    A(int _n) : n(_n){ cout << n << endl; };
};

struct B {
    A a = 10;
    B(int _n) : a(_n){};
    B(){ a = 30; };
};

int main(){
    B b1, b2(20);
}
```

## 문제5
다음 프로그램의 출력과 static 멤버에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

class Counter
{
    static int count;
    int n;

public:
    Counter(int _n):n(_n){ cout << n << ":" << ++count << endl; };
    ~Counter(){ cout << n << ":" << --count << endl; };
};

int Counter::count = 0;

void A(){ Counter c1(1), c2(2); }
void B(){ Counter c3(3), c4(4); A(); }

int main(){
    B();

//  cout << Counter::count << endl;
}
```
