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
### 데이터의 수 : &nbsp;![equation](http://latex.codecogs.com/svg.latex?n)
* ### Worst case (최악의 경우)
    - ### 연산 기준 : &nbsp;= (나머지 연산은 '='에 의존적)
    - ### 시간 복잡도(Time Complexity) : &nbsp;![equation](http://latex.codecogs.com/svg.latex?T(n)%20=%20n)
    - ### Big-O : &nbsp;![equation](http://latex.codecogs.com/svg.latex?O(n))

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
### 데이터의 수 : &nbsp;![equation](http://latex.codecogs.com/svg.latex?n)
* ### Worst case (최악의 경우)
    - ### 연산 기준 : &nbsp;= (나머지 연산은 '='에 의존적)
    - ### 시간 복잡도(Time Complexity)
        > #### n이 1이 될 때 2로 나눈 횟수 ![equation](http://latex.codecogs.com/svg.latex?k)
        > #### 데이터가 하나 남을 때 횟수 1
    ![equation](http://latex.codecogs.com/svg.latex?T(n)%20=%20k%20&plus;%201)  
    ![equation](http://latex.codecogs.com/svg.latex?n%20%5Ctimes%20%5Cleft%20(%20%5Cfrac%7B1%7D%7B2%7D%20%5Cright%20)%5Ek%20=%201)  
    ![equation](http://latex.codecogs.com/svg.latex?%5Clog_2%20n%20=%20k)  
    ![equation](http://latex.codecogs.com/svg.latex?T(n)%20=%20%5Clog_2%20n)  
    - ### Big-O : &nbsp;![equation](http://latex.codecogs.com/svg.latex?%5Clog_2%20n)