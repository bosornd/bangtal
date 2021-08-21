---
title: "12주차 퀴즈"
permalink: /lectures/c++/quiz12/
---

## 문제1
주어진 자료형 배열에서<br />
최대/최소값을 출력하는 템플릿 함수 MAX와 MIN을 작성하세요(2점).

```c
#include <iostream>
using namespace std;

// insert your code here

int main(){
    char buf[] = "partytime";

    cout << MAX<char>(buf, 9) << endl;
    cout << MIN<char>(buf, 9) << endl;
}
```

## 문제2
문자열("hello world")의 길이(11)가 출력되도록<br />
다음 프로그램을 수정하세요(2점).

```c
#include <iostream>
#include <cstring>
using namespace std;

template <typename T>
int LENGTH(T object){
    return sizeof(object);
}

// insert your code here

int main(){
    char buf[] = "hello world";
    cout << LENGTH(buf) << endl;

    char *buf2 = buf;
    cout << LENGTH(buf2) << endl;

    string buf3 = "hello world";
    cout << LENGTH(buf3) << endl;
}
```

## 문제3
주어진 자료형의 배열을 다루는 Array 클래스를 완성하세요(4점).

```c
#include <iostream>
using namespace std;

template <typename T>
class Array {
    // insert your code here
};

int main(){
    Array<int> a;
    a.push(10); a.push(20); a.push(30);

    cout << a.pop();    // 30
    cout << a.pop();    // 20
    cout << a.pop();    // 10
}
```

## 문제4
다음 프로그램의 출력에 대해서 설명하세요(2점).

```c
#include <iostream>
using namespace std;

template <typename T, const T* LIST, int SIZE, T(*FUNC)(T)>
struct Composed {
    T sum() {
        T result = 0;
        for (int i = 0; i < SIZE; ++i) {
            result += FUNC(LIST[i]);
        }
        return result;
    }
};

int numbers[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
int square(int i) { return i * i; }

int main()
{
    Composed<int, numbers, 10, square> c;
    cout << c.sum() << endl;
}
```
