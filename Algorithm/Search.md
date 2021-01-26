탐색 (Search)
==============
## 순차 탐색 (Linear Search; Sequential Search)
------------------------------------------------
```C
#include <stdio.h>

int LSearch(int ar[], int len, int target) // 순차 탐색 함수
{
    for(int i = 0; i < len; i++)
    {
        if(ar[i] == target)
            return i;
    }

    return -1; //탐색 대상이 없을 시 -1 반환
}

int main()
{
    int arr[] = {3, 5, 2, 4, 9};

    int idx = LSearch(arr, sizeof(arr) / sizeof(int), 4);
    if(idx == -1)
        printf("Fail\n");
    else
        printf("Index : %d\n", idx);
}
```
### 데이터의 수 : &nbsp;$n$
* ### Worst case (최악의 경우)
    - ### 연산 기준 : &nbsp;= (나머지 연산은 '='에 의존적)
    - ### 시간 복잡도(Time Complexity) : &nbsp;$T(n) = n$
    - ### Big-O : &nbsp;$O(n)$

## 이진 탐색 (Binary Search)
---------------------------------------
```C
#include <stdio.h>

int BSearch(int ar[], int len, int target) // 이진 탐색 함수
{
    int first = 0;
    int last = len - 1;
    int mid;

    while (first <= last)
    {
        mid = (first + last) / 2;

        if(target = ar[mid])
            return mid;
        else if(target < ar[mid])
            last = mid - 1;
        else
            first = mid + 1;
    }

    return -1; //탐색 대상이 없을 시 -1 반환
}
```
### 데이터의 수 : &nbsp;$n$
* ### Worst case (최악의 경우)
    - ### 연산 기준 : &nbsp;= (나머지 연산은 '='에 의존적)
    - ### 시간 복잡도(Time Complexity)
        > #### n이 1이 될 때 2로 나눈 횟수 $k$
        > #### 데이터가 하나 남을 때 횟수 1
    $$T(n) = k + 1$$
    $$n \times \left(\frac{1}{2}\right) ^ k = 1$$
    $$n = 2^k$$
    $$\log_2 n = k$$
    $$T(n) = \log_2 n$$
    - ### Big-O : &nbsp;$O($log_2 n$)$