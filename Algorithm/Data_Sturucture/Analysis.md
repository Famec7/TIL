알고리즘 분석 (Analysis of Algorithm)
====================================
## 공간 복잡도 (Space Complexity)
-----------------------------------
* ### 분석 대상 : 메모리 사용량
* ### 메모리 사용량이 적을수록 좋은 알고리즘

## 시간 복잡도 (Time Complexity)
----------------------------------------
* ### 분석 대상 : **실행 속도** (즉 연산횟수)
* ### 실행 시간이 짧을수록 즉 연산횟수가 적을수록 좋은 알고리즘
* ### 연산횟수를 세는 기준은 의존적인 연산은 포함하지 않고 계산
* ### 최악의 경우(worst case)와 평균적인 경우(average case)로 나뉘어서 계산이 가능함
* ### 보통은 **worst case**로 계산하는 경우가 많음 (average case는 평균을 구하기가 힘듦)

## 공간 복잡도 vs 시간 복잡도
-----------------------------------------
* ### 메모리 사용량이 적고 실행 속도가 적으면 좋은 알고리즘
* ### 하지만 둘 다 만족하는 알고리즘을 계산하기 어려움
* ### 보통은 **시간 복잡도**를 위주로 알고리즘을 판별

## Big-O (빅오 표기법)
-----------------------------------------
* ### 데이터 수에 따른 증가율 추세를 보기위한 표현법
* ### 데이터의 수가 $n$이고 증가 추세가 $n$이면 $O(n)$으로 표기한다.
* ### 대표적인 빅오 표기법
    - #### ![equation](http://latex.codecogs.com/svg.latex?O(1)) 상수형 빅오 :&nbsp; 연산횟수가 상수일 때 사용된다.(Ex. 연산횟수가 1, 3, 5, etc.)
    - #### ![equation](http://latex.codecogs.com/svg.latex?O(%5Clog%20n)) 로그형 빅오 :&nbsp; 가장 이상적인 알고리즘 즉, 데이터 수가 많을 수록 증가 추세가 줄어드는 유형
    - #### ![equation](http://latex.codecogs.com/svg.latex?O(n)) 선형 빅오 :&nbsp; 데이터 수와 비례관계
    - #### ![equation](http://latex.codecogs.com/svg.latex?O(n%5Clog%20n)) 선형로그형 빅오
    - #### ![equation](http://latex.codecogs.com/svg.latex?O(n%5E2)) :&nbsp; 중첩반복문에서 나오는 알고리즘, 바람직하지 않은 알고리즘
    - #### ![equation](http://latex.codecogs.com/svg.latex?O(n%5E3))
    - #### ![equation](http://latex.codecogs.com/svg.latex?O(2%5En)) 지수형 빅오 :&nbsp; 사용하지 않는 알고리즘