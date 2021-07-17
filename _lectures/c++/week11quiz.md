---
title: "11주차 퀴즈"
permalink: /lectures/c++/quiz11/
---

## 문제1
다음 프로그램의 출력과 가상 함수에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

struct TP1 {
    void print(){ cout << "1" << endl; };
};

struct TP2 : public TP1 {
    virtual void print(){ cout << "2" << endl; };
};

struct TP3 : public TP2 {
    void print(){ cout << "3" << endl; };
};

struct TP4 {
    void print(){ cout << "4" << endl; };
};

struct TP5 : public TP3, public TP4 {
    void print(){ cout << "5" << endl; };
};

int main(){
    TP5 p5; p5.print();
    TP4& p4 = p5; p4.print();
    TP3& p3 = p5; p3.print();
    TP2& p2 = p5; p2.print();
    TP1& p1 = p5; p1.print();
}
```

## 문제2
다음 프로그램의 문제와 해결 방법에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

struct A {
    A(){ cout << "A constructed" << endl; };
    ~A(){ cout << "A destructed" << endl; };
};

struct B : public A {
    B(){ cout << "B constructed" << endl; };
    ~B(){ cout << "B destructed" << endl; };
};

struct C : public B {
    C(){ cout << "C constructed" << endl; };
    ~C(){ cout << "C destructed" << endl; };
};

int main()
{
    A* a = new C;
    delete a;
}
```

## 문제3
Time, Date, Now 클래스를<br />
다음 클래스 다이어그램에 따라 구현하세요(4점).

<figure>
  <img src="/assets/images/class_diagram_time_date.png">
</figure>

```c
#include <iostream>
using namespace std;

// insert your code here

int main()
{
    Now n(2021, 10, 7, 13, 27, 22);   // 2021년 10월 7일 13:27:22
    n.print();

    return 0;
}
```

## 문제4
다음 프로그램의 출력은(2점)?

<figure>
  <img src="/assets/images/class_diagram_time_date.png">
</figure>

```c
#include <iostream>
using namespace std;

#define DBG(str) cout << str << endl

class Integer {
    int n;
public:
    Integer(int _n) : n(_n){ DBG("A"); };
    Integer(const Integer& i) : n(i.n){ DBG("B"); };

    Integer& operator=(const Integer& i){ DBG("C"); n = i.n; return *this; };
    Integer& operator+=(const Integer& i){ DBG("D"); n += i.n; return *this; };

    friend Integer operator+(const Integer& a, const Integer& b);
    friend Integer operator*(const Integer& a, const Integer& b);
    friend ostream& operator<<(ostream& os, const Integer& i);

};

Integer operator+(const Integer& a, const Integer& b){
    DBG("E"); return Integer(a.n + b.n);
}
Integer operator*(const Integer& a, const Integer& b){
    DBG("F"); return Integer(a.n * b.n);
}
ostream& operator<<(ostream& os, const Integer& i){
    DBG("G"); os << i.n; return os;
}

int main(){
    Integer n1(1), n2(2);
    Integer n = 5 + n1 + 2 * n2;

    cout << n << endl;
}
```
