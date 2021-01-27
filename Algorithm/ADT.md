추상 자료형 (ADT; Abstract Data Type)
=======================================
- ### 정의 : 구체적인 처리과정이 아닌 **기능**을 나열한 것
- ### 즉 구현의 세부과정이 아닌 **데이터**와 데이터를 처리하는 **기능**을 명시
- ### 보통 객체지향언어에서 사용됨 (Ex. C++의 class)
- ### **자료**와 자료를 처리할 수 있는 **기능**이 필요함

단순 연결 리스트의 ADT 예시
```C++
#include <iostream>
#include <functional>
using namespace std;

template <typename T>
class List{
private: // 자료 정의, 사용자는 자료에 접근할 수 없음
    T data;
    List *plist = nullptr;
    int opCount = 0;

public: // 기능 구현, 사용자는 기능을 사용함으로써 자료구조 활용이 가능해짐
    List() { /*초기화*/ }
    void LInsert() { /*데이터 삽입*/ }
    bool LFirst { /*첫 번째 데이터 참조*/ }
    bool LNext { /*다음 데이터 참조*/ }
    T LRemove { /*데이터 삭제 후 반환*/ }
    int LCount { /*생성된 객체 카운트*/ }
    void SetSortRule(List *plist, function<T(T, T)> param) { /*정렬기준*/ }
}

int main()
{
    // 사용자 코드
}
```
- ### 자료의 접근은 제어하지만, 자료를 다룰 수 있는 기능(함수)를 제공
- ### C++은 STL에 ADT가 구현되어있음 즉, STL은 거의 필수
- ### 자료구조의 공부는 3가지 순서로 나눌 수 있음
    - ### ADT 파악
    - ### ADT 구현
    - ### ADT 활용