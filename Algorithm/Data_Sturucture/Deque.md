덱 (Deque; double-ended queue)
==============================
## 원리
-------
- ### 앞, 뒤로 데이터를 넣고 뺄 수 있는 구조이다.

## 양방향 리스트 기반 덱
-------------------------
### 특징
- #### front_ptr과 back_ptr로 맨 앞과 맨 뒤 노드를 가리킨다.
- #### 양방향 리스트와 비슷하다. (거의 똑같다.)

### 코드
-------
Node.h
```C++
#pragma once

template <typename T>
class Node
{
    template <typename T1>
    friend class Deque;
private:
    T data;
    Node<T> *next = nullptr;
    Node<T> *prev = nullptr;

public:
    T GetData() const { return data; }
};
```
Deque.h
```C++
#pragma once
#include <iostream>
#include "Node.h"

using namespace std;

template <typename T>
class Node;

template <typename T>
class Deque
{
private:
    int count = 0;
    Node<T> *front_ptr = nullptr;
    Node<T> *back_ptr = nullptr;

public:
    bool empty()
    {
        if (front_ptr == nullptr)
            return true;
        else
            return false;
    }

    void push_front(T data)
    {
        Node<T> *newNode = new Node<T>;
        newNode->data = data;
        newNode->next = front_ptr;

        if (empty())
            back_ptr = newNode;

        else
            front_ptr->prev = newNode;

        front_ptr = newNode;
        count++;
    }

    void push_back(T data)
    {
        Node<T> *newNode = new Node<T>;
        newNode->data = data;
        newNode->prev = back_ptr;

        if (empty())
            front_ptr = newNode;

        else
            back_ptr->next = newNode;
        
        back_ptr = newNode;
        count++;
    }

    void pop_front()
    {
        if (empty())
        {
            cout << "ERROR: Memory Is Not Exist" << endl;
            exit(-1);
        }

        Node<T> *pDelete = front_ptr;
        front_ptr = front_ptr->next;
        delete pDelete;

        if(front_ptr == nullptr)
            back_ptr = nullptr;
        else
            front_ptr->prev = nullptr;

        count--;
    }

    void pop_back()
    {
        if (empty())
        {
            cout << "ERROR: Memory Is Not Exist" << endl;
            exit(-1);
        }

        Node<T> *pDelete = back_ptr;
        back_ptr = back_ptr->prev;
        delete pDelete;

        if(back_ptr == nullptr)
            front_ptr = nullptr;
        else
            back_ptr->next = nullptr;

        count--;
    }

    T front() const { return front_ptr->data; }
    T back() const { return back_ptr->data; }
    int size() const { return count; }
};
```
Deque.cpp
```C++
#include <iostream>
#include "Deque.h"

using namespace std;

int main()
{
    Deque<int> d;

    d.push_front(1);
    d.push_front(2);
    d.push_front(3);
    d.push_back(4);
    d.push_back(5);

    cout << "Size: " << d.size() << endl;

    while (!d.empty())
    {
        cout << d.front() << endl;
        d.pop_front();
    }
        
    return 0;
}
```

## ADT와 원리
------------
- ### 양방향 리스트와 구현방식이 같다.