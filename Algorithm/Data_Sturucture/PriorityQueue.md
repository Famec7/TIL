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