우선순위 큐 (Priority Queue)
===============================
## 원리
-----------
- ### 일반 큐와 달리 우선순위가 높은 값이 먼저 나오는 원리
- ### 큐 (Queue)와 마찬가지로 배열, 리스트를 이용해서 구현이 가능함
- ### 하지만 일반적으로 배열을 이용한 힙을 이용하여 구현

## 힙을 이용하는 이유
-----------------------
|구조|push|pop|
|------|---|---|
|배열|O(n)|O(1)|
|리스트|O(n)|O(1)|
|힙|![equation](http://latex.codecogs.com/svg.latex?O(log_2%7Bn%7D))| ![equation](http://latex.codecogs.com/svg.latex?O(log_2%7Bn%7D))|

- ### 자료 저장 및 삭제에 대한 성능에서 차이가 크다.
- ### 힙의 시간 복잡도는 [힙 (Heap)](https://github.com/Famec7/TIL/blob/main/Algorithm/Data_Sturucture/Heap.md)을 참고하면 된다.
- ### 힙을 배열로 구현하는 이유는 마지막 노드 추가 시 마지막 노드를 탐색하는데 용이하기 때문이다.

## 소스 코드(구현)
-------------------
[힙 (Heap)](https://github.com/Famec7/TIL/blob/main/Algorithm/Data_Sturucture/Heap.md)에서 구현한 코드가 우선순위 큐와 원리가 같은 코드이기 때문에 코드가 같다.

## STL
---
queue를 include하여 이용하면 됩니다.  
std 네임스페이스에 속합니다.
```C++
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int main()
{
    priority_queue<int, vector<int>, less<int>> q;

    q.push(2);
    q.push(3);
    q.push(1);
    q.push(5);
    q.push(4);

    while (!q.empty())
    {
        cout << q.top() << endl;
        q.pop();
    }

    return 0;
}
```
- ### priority\_queue<자료형>과 priority\_queue<자료형, 컨테이너, 정렬기준>으로 선언이 가능합니다.
- ### priority\_queue<자료형>으로 선언 시 컨테이너는 vector가 default이며, 정렬기준은 내림차순입니다.
- ### 정렬 기준은 기본적으로 less(내림차순)과 greater(오름차순)이 있으며, 아래 코드처럼 연산자를 다중 정의(overloading)하여 직접 만들어서 사용할 수도 있습니다.

```C++
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

struct cmp
{
    bool operator()(int data1, int data2){
        return data1 > data2;
    }
};

int main()
{
    priority_queue<int, vector<int>, cmp> q;

    q.push(2);
    q.push(3);
    q.push(1);
    q.push(5);
    q.push(4);

    while (!q.empty())
    {
        cout << q.top() << endl;
        q.pop();
    }

    return 0;
}
```

- ### 메서드    
    - #### push : 값을 저장합니다. operator의 우선 순위에 맞추어서 저장합니다.
    - #### pop : top에 있는 값을 삭제합니다.
    - #### top : 맨 위 값을 반환합니다.
    - #### empty : 노드가 비어있을 시 true, 아닐 시 false를 반환합니다.
    - #### size : 원소의 개수를 반환합니다.
    - #### swap : 두 우선순위 큐를 서로 교환합니다. (C++11)
    - #### emplace : 컨테이너 내부에서 값을 저장합니다. (C++11)