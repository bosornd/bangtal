---
title: "5주차 퀴즈"
permalink: /lectures/c++/quiz05/
---

## 문제1
다음의 예로,<br />객체 지향의 특징 중에서 추상화의 개념에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

class Student
{
private:
    string m_name;

public:
    Student(const string &n) : m_name(n){ };
    const string& name(){ return m_name; };
};

int main()
{
    Student s1("tom"), s2("jane");

    cout << s1.name() << endl;
    cout << s2.name() << endl;

    return 0;
}
```

## 문제2
다음의 예로,<br />객체 지향의 특징 중에서 캡슐화의 개념에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

class Rect {
private:
    int width, height;

public:
    Rect(int w, int h) : width(w), height(h){};
    int Area() const { return width * height; };
};

int main()
{
    Rect r(10, 20);
    cout << r.Area() << endl;

    return 0;
}
```

## 문제3
국어, 영어, 수학 점수를 저장(멤버 변수)하고, 총점과 평균을 출력<br />
(멤버 함수)하도록 문제1의 Student 클래스를 확장하세요.<br />
다음 메인 함수에서 사용하는 데에 문제가 없어야 합니다(6점).

```c
#include <iostream>
using namespace std;

class Student
{
public:
    Student(const string &n) : m_name(n){ };
    const string& name(){ return m_name; };

private:
    string m_name;

    // insert your code here
};

int main(){
    Student s1("tom");

    s1.setKorean(85);
    s1.setEnglish(80);
    s1.setMath(95);

    cout << "total: " << s1.getTotal() << endl;
    cout << "average: " << s1.getAverage() << endl;
}
```
