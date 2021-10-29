---
title: "10주차 퀴즈"
permalink: /lectures/c++/quiz10/
---

## 문제1
다음의 예로,<br />객체 지향의 특징 중에서 상속의 개념에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

class Person {
    string name;

public:
    Person(const string& n) : name(n){};
};

class Student : public Person {
    int number;
    
public:
    Student(int n, const string& name) : Person(name),  number(n){};
};

int main()
{
    Student s(1, "tom");

    return 0;
}
```

## 문제2
다음 클래스 다이어그램을 설명하세요(2점).<br />
Subject(과목), Major(전공 과목), General(교양 과목), prerequisite(선수 과목)

<figure>
  <img src="/assets/images/class_diagram_courses.png">
</figure>

## 문제3
다음 클래스를 C++로 구현하세요(4점).<br />
C++언어가 C언어를 선수 과목으로 가지는 것을 표현하고<br />
이를 출력합니다.

<figure>
  <img src="/assets/images/class_diagram_courses2.png">
</figure>

```c
#include <iostream>
using namespace std;

// insert your code here

int main()
{
    Major c("C언어"), cpp("C++", &c);

    c.Print();
    cpp.Print();

    return 0;
}
```

## 문제4
다음 프로그램의 출력과 생성자/소멸자의 호출에 대해서 설명하세요(2점).

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
    C c1;
}
```
