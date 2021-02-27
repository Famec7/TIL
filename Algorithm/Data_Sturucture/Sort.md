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