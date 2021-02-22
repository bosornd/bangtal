---
title: "14주차 퀴즈"
permalink: /lectures/c/quiz14/
---

## 문제1
다음 프로그램의 출력은(1점)?<br />
construct, add, print 함수가 어떻게 동작하는 지를 설명하세요(3점).<br />
할당된 메모리를 모두 반납하는 destruct 함수를 완성하세요(2점).

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int value;
    Node* next;
};

Node* construct(int v = 0)
{
    Node* n = (Node*)malloc(sizeof(Node));
    n->value = v;
    n->next = NULL;
    return n;
}

Node* add(Node* root, int v)
{
    if (root->next == NULL || root->value > v) {
        Node* n = construct(v);
        n->next = root;
        root = n;
    }
    else {
        root->next = add(root->next, v);
    }
    return root;
}

void print(Node* root)
{
    for(Node* n = root; n->next != NULL; n = n->next)
        printf("%d ", n->value);
    printf("\n");
}

void destruct(Node* root)
{
    // insert code here
}

int main()
{
    Node* root = construct();

    root = add(root, 5);
    root = add(root, 9);
    root = add(root, 2);
    root = add(root, 7);

    print(root);

    destruct(root);
}
```
## 문제2
명령어 라인으로 주어진 파일의 내용이 동일한 지를 검사하는 프로그램을 작성하세요(2점).

```
C:\> Compare.exe a.txt a.txt
a.txt와 a.txt는 동일합니다.

C:\> Compare.exe a.txt b.txt
a.txt와 b.txt는 서로 다릅니다.

C:\>
```

## 문제3
추가 설명이 필요한 것을 알려주세요.
