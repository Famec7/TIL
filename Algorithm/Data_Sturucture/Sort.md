정렬
=====
- ## stablity (안정성)
-------------------
- ### 같은 값을 가진 원소끼리 swap이 되면 unstable sort, swap이 되지 않을 시 stable sort라고 부름

- ## 버블 정렬 (Bubble sort)
------------------
- ### 원리
    - #### 인접한 인덱스의 데이터끼리 비교하여 swap을 진행하는 방식이다. 우선순위가 낮은 데이터를 맨 뒤로 보내는 작업을 데이터의 개수 - 1만큼 수행한다.
    <center><img src = "./img/BubbleSort.JPG"></center>

- ### 소스 코드 (구현)
```C++
#include <iostream>
#include <algorithm>
#include <functional>

using namespace std;

template <typename T>
void bubble_sort(T *start, T *end, function<bool(T data1, T data2)> cmp = [](T data1, T data2) { return data1 < data2; })
{
    for (T *pos = start; pos < end - 1; pos++)
    {
        for (T *pos2 = start; pos2 < end - pos + start; pos2++)
        {
            if (cmp(*(pos2 + 1), *pos2))
                swap(*pos2, *(pos2 + 1));
        }
    }
}

int main()
{
    int arr[7] = {78, 4, 6, 51, 7, 81, 14};

    bubble_sort(arr, arr + 6);

    for (const auto r : arr)
    {
        cout << r << ' ';
    }

    return 0;
}
```

- ### 성능
    - #### Big O를 계산할 때에는 보통 '비교 횟수'에 대해서 검사를 진행한다. 위 코드의 비교 연산은 if문이다. 반복문만큼 비교 횟수가 일어나므로 (n - 1) + (n - 2) + (n - 3) + ... + 1 만큼 비교 연산이 실행된다. 이 등차수열의 합은 n(n - 1) / 2이다. 즉, 버블 정렬의 Big O는 O(n^2)이다. best case는 단 한 번의 이동이 일어나지 않으나 worst case는 최악의 성능을 일으킨다.

    - #### stable sort이다.

- ## 선택 정렬 (Selection sort)
----------
- ### 원리
    - #### 기준에 맞추어서 데이터를 선택(selection)하면서 옮기는 작업을 수행하는 정렬이다.데이터를 선택하는 하나의 별도 메모리 공간이 필요하다.
    <center><img src = "./img/SelcSort.JPG"></center>

- ### 소스 코드 (구현)
```C++
#include <iostream>
#include <algorithm>
#include <functional>

using namespace std;

template <typename T>
void selection_sort(T *start, T *end, function<bool(const T data1, const T data2)> cmp = [](const T data1, const T data2) { return data1 < data2; })
{
    T *ptr = nullptr;

    for (T *pos = start; pos < end - 1; pos++)
    {
        ptr = pos;
        for (T *pos2 = pos + 1; pos2 < end; pos2++)
        {
            if(cmp(*pos2, *ptr))
                ptr = pos2;
        }

        swap(*pos, *ptr);
    }
}

int main()
{
    int arr[5] = {13, 11, 51, 2, 7};

    selection_sort(arr, arr + 5);

    for (const auto r : arr)
    {
        cout << r << ' ';
    }

    return 0;
}
```

- ### 성능
    - #### 데이터의 비교횟수는 버블 정렬(bubble sort)와 마찬가지로 O(n^2)이지만 이동횟수는 안쪽 for문 바깥에 존재하므로 n-1의 교환이 일어난다. 즉 비교연산에 대한 Big O는 O(n^2), 이동연산에 대한 Big O는 O(n)이다.

    - #### unstable sort이다.

- ## 삽입 정렬 (Insertion sort)
-------------
- ### 원리
    - #### 인덱스가 1인 데이터부터 앞 인덱스에서 맞는 위치를 찾아 삽입하면서 정렬하는 방식이다. 이 과정에서 데이터를 삽입하기 위해 배열을 한칸씩 미는 작업이 필요하다.
    <center><img src = "./img/InsertSort.JPG"></center>

- ### 소스 코드 (구현)
```C++
#include <iostream>
#include <functional>

using namespace std;

template <typename T>
void insertion_sort(T *start, T *end, function<bool(const T data1, const T data2)> cmp = [](const T data1, const T data2){ return data1 > data2; })
{
    T *insert_data = new T;

    for (T *pos = start + 1; pos < end; pos++)
    {
        T *pos2 = nullptr;
        *insert_data = *pos;

        for (pos2 = pos - 1;  pos2 >= start; pos2--)
        {
            if(cmp(*pos2, *insert_data))
                *(pos2 + 1) = *pos2;
            else
                break;
        }

        *(pos2 + 1) = *insert_data;
    }
}

int main()
{
    int arr[5] = {13, 11, 51, 2, 7};

    insertion_sort(arr, arr + 5);

    for (const auto r : arr)
    {
        cout << r << ' ';
    }

    return 0;
}
```

- ### 성능
    - #### worst case이면 안 쪽 for문의 조건을 탈출하지 못하고 끝까지 수행하므로 버블 정렬과 같은 O(n^2)의 결과가 나온다. 하지만 best case이면 O(n)의 결과가 나온다.
    - #### stable sort이다.