---
title: "13주차 퀴즈"
permalink: /lectures/c++/quiz13/
---

## 문제1
다음 프로그램을 예로 STL(Standard Template Library)의<br />
container, iterator, algorithm, functor(function object)에 대해서 설명하세요(2점).

```c
#include <iostream>     // std::cout
#include <vector>       // std::vector
#include <algorithm>    // std::transform
#include <functional>   // std::plus
using namespace std;

int main(){
    vector<int> a{ 1, 2, 3, 4, 5 }, b{ 6, 7, 8, 9, 10 }, c(5);
    transform(a.begin(), a.end(), b.begin(), c.begin(), plus<int>());
    for(vector<int>::iterator it = c.begin(); it != c.end(); ++it)
        cout << *it << endl;
    return 0;
}
```

## 문제2
다음 프로그램에서,<br />
입력된 key 값에 매핑되는 숫자를 반환하는 함수 search()를 완성하세요(2점).

```c
#include <iostream>
#include <vector>
using namespace std;

struct Pair {
    string key;
    int value;
};

int search(const vector<Pair>& v, const string& k){
    // insert your code here
}

int main(){
    vector<Pair> v;
    v.push_back(Pair{"a", 10});
    v.push_back(Pair{"b", 20});
    v.push_back(Pair{"c", 30});
    v.push_back(Pair{"d", 40});
    v.push_back(Pair{"e", 50});

    string k;
    cin >> k;

    cout << search(v, k) << endl;
}
```

## 문제3
다음 프로그램의 출력에 대해서 설명하세요(2점).

```c
#include <iostream>     // std::cout
#include <algorithm>    // std::copy
#include <vector>       // std::vector
using namespace std;

int main(){
    vector<int> v = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    copy(v.begin() + 3, v.end(), v.begin());
    for(int i:v) cout << i;

    return 0;
}
```

## 문제4
리스트에 421보다 큰 수가 몇 개나 존재하는 지를 출력하는<br />
다음 프로그램을 완성하세요(2점).

```c
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

int main(){
    vector<int> v(1000);
    generate(v.begin(), v.end(), []()->int { return rand() % 1000; });

    cout << "how many numbers more than 421 are in the list? ";
    cout << /* insert code here only */ << endl;

    return 0;
}
```
