# 배열 List 1



## 🎲알고리즘

> 유한한 단계를 통해 문제를 해결하기 위한 절차나 방법
>
> 주로 컴퓨터 용어로 쓰이며, 컴퓨터가 어떤 일을 수행하기 위한 단계적 방법
>
> 어떠한 문제를 해결하기 위한 절차



### 컴퓨터 분야에서 알고리즘을 표현하는 방법

1. 슈더코드(의사코드)와 순서도
   1. 문법에 맞지는 않지만 개념을 담은 의사 코드



### 무엇이 좋은 알고리즘일까?

1. 정확성
   - 얼마나 정확하게 동작하는가
2. 작업량
   - 얼마나 적은 연산으로 원하는 결과를 얻어내는가
   - 시간 복잡도와 관련
3. 메모리 사용량
   - 얼마나 적은 메모리를 사용하는가
4. 단순성
   - 얼마나 단순한가
5. 최적성
   - 더 이상 개선할 여지 없이 최적화 되었는가



### 알고리즘의 성능 축정하기

- 성능 분석의 기준으로 알고리즘의 작업량을 비교한다.
- 알고리즘의 작업량을 표현할 때 시간 복잡도로 표현한다



#### 시간 복잡도 (Time complexity)

- 실행되는 명령문의 개수를 계산
  - 대입과 연산



#### 빅-오(O) 표기법 (Big-Oh Notation)

- 시간 복잡도 함수 중에서 가장 큰 영향력을 주는 n에 대한 항만을 표시 (최고 차항)
- 계수는 생략한다.
- 최악의 경우
- 빅 세타 (최선), 빅 오메가(평균)

![big o notation](https://i.imgur.com/yOEbMzp.jpg)





## 💎배열

>  일정한 자료형의 변수들을 하나의 이름으로 열거하여 사용하는 자료구조



### 배열의 필요성

- 프로그램 내에서 여러 개의 변수가 필요할 때 , 일일이 다른 변수명을 이용하여 자료에 접근하는 것은 비효율적
- 배열을 사용하면 하나의 선언을 통해 둘 이상의 변수를 선언할 수 있다
- 다수의 변수로는 하기 힘든 작업을 배열을 활용해 쉽게!



### 1차원 배열의 선언

- 별도의 선언 방법이 없으면 변수에 처음 값을 할당할 때 생성
- 이름 : 프로그램에서 사용할 배열의 이름
- 같은 자료형 & 크기 선언



```python
# 1차원 배열 선언의 예
Arr = list()
Arr = []

# 다른 언어처럼 자료형, 크기를 정하려면,
Arr = [0]*5
```



### 1차원 배열의 접근

- list_name[index]
- 파이썬에서는 음수 index를 사용할 수 있다 
- 음수 인덱스 때문에 원하지 않는 값이 나오지 않게 if 문으로 분기





---



## 정렬

> 2개 이상의 자료를 특정 기준에 의해 작은 값부터 큰값(오름차순) 혹은 그 반대의 순서(내림차순) 재배열



- 버블 정렬 (Bubble Sort)
- 카운팅 정렬 (Counting Sort)
- 선택 정렬 (Selection Sort)
- 퀵 정렬 (Quick Sort)
- 삽입 정렬 (Insertion Sort)
- 병합 정렬 (Merge Sort)



### 1 버블 정렬 (Bubble Sort)

> 인접한 두 개의 원소를 비교하며 자리를 계속 교환하는 방식



### 과정

1. 첫 번째 원소부터 인접한 원소끼리 계속 자리 교환해 마지막 자리까지 이동
2. 한 단계가 끝나면 가장 큰 원소가 마지막 자리로 정렬



### 시간 복잡도

O(n^2)





### 2 카운팅 정렬 (Counting Sort)

> 항목들의 순서를 결정하기 위해 집합에 각 항목이 몇개 씩 있는지 세는 작업을 한다.
>
> 선형 시간에 정렬한다. O(n)



- 제한
  - 정수로 표현할 수 있는 자료에 대해서만 적용 가능
  - 발생 횟수를 기록하기 때문에 
  - 정수로 인덱스되는 카운트의 배열을 사용하기 때문
  - 가장 큰 정수를 알아야 배열의 크기를 선언할 수 있다



### 과정

1. 원본의 값이 등장하는 횟수를 counting 하는 배열을 선언하고 누적합을 구한다
2. 원본을 뒤에서부터 순회한다
3. 원본의 값을 인덱스로 하여 횟수를 counting 배열에서 찾는다
4. counting 배열의 값을 -1한 값을 인덱스로 하여 정렬된 배열의 값을 정한다. 



- 안정정렬
  - 뒤에서 부터 정렬하면서
  - 원래 배열의 index를 순서를 보존하며 정렬한다



### 시간복잡도

- n은 리스트의 길이, K는 정수의 최대값
- O(n+k)







## ✨완전 검색✨

> 문제의 해법으로 생각할 수 있는 모든 경우의 수를 나열하고 확인한다
>
> Brute-force
>
> Generate-and-Test
>
> 모든 경우의 수를 테스트하고 최종 해법을 도출한다. (경우의 수가 작을 때 유리하다)



- 수행속도는 느리지만
- 해답을 찾아낼 확률이 높다
- 우선 완전 검색 접근으로 해답을 도출하고 >> 성능 개선



### Baby-jin Game

- triplet : 3장의 카드가 동일한 번호
- run : 연속된 카드
- baby-gin : 6장의 카드가 run과 triplet으로 구성된 경우
- 6장의 숫자를 입력받아 baby-gin 판별



### 순열(Permutation)

- 서로 다른 것들 중 몇 개를 뽑아서 한 줄로 나열하는 것
- nPr
- nPn = n! (Factorial)

```python
card = [4, 5, 6,]
N = 3

for i in range(N):
    for j in range(N):

        # 중복 순열 아니기 때문에
        if j == i : continue

        for k in range(N):

            if k != i and k != j:
                print(card[i], card[j], card[k])
```





## 그리디 (Greedy Algorithm)

> 최적해를 구하는 데 사용되는 근시안적인 방법
>
> 여러 경우 중 하나를 결정할 때, 그 순간에 최적이라고 생각하는 것을 선택한다.
>
> 지역적으로는 최적이지만 최종적인 해답이 항상 최적이라는 보장은 없다.



### 과정

1. 해 선택
   1. 멀리 내다보지 않고 가장 좋은 해를 선택한다.
   2. 최고 한도로 
2. 실행 가능성 검사
   1. 조건에 만족하는지 검사한다
3. 해 검사
   1. 최선이 아니라면 해 선택으로 돌아간다.



### baby-gin을 greedy로 풀어보면?

- 6개 숫자는 6자리의 정수 값
- 0~9까지 정수로 counts 배열을 만든다
- 원본 배열의 값의 등장 횟수를 counts에 기록한다.

