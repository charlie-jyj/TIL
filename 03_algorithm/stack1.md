# Stack 1



## 스택

> 물건을 쌓아 올리듯 자료를 쌓아 올린 형태의 자료 구조



- 선형 구조
  - 자료 간의 관계가 1:1 관계
  - 비선형 구조
    - 자료 간의 관계가 1: N 관계 (트리)
  - 순환 (그래프)
  
- 스택에 자료를 삽입하거나 스택에서 자료를 꺼낼 수 있다
- 마지막에 삽입한 자료를 가장 먼저 꺼낸다
  - Last In First Out



### 스택을 구현하기 위해서 필요한 자료 구조와 연산

#### 자료구조

> 자료를 선형으로 저장할 저장소

- c 언어에서는 배열을 사용, python은 List 사용
- 저장소 자체를 스택이라 부르기도 한다
- 스택에서 마지막 삽입된 원소 위치 = top
  - 보통 인덱스 -1 로 초기한다.



#### 연산

- 삽입: `push`
  - top을 +1 하고 값을 넣는다
- 삭제: `pop`
  - 삽입한 자료의 역순으로 꺼낸다
  - top 의  item을 제거하고 top을 -1 한다.
- 공백인지 확인: `isEmpty`
  - 길이가 0
- top 의 item을 반환 : `peek`
  - 데이터를 꺼내지는 않고 값만 반환한다



#### stack : push 알고리즘

- append 메소드로 리스트의 마지막에 데이터 삽입
- 리스트는 크기가 가변적이지만 배열의 경우 크기가 고정되어 있으므로 overflow하지 않도록 주의

```python
def push(item):
	s.append(item)
```



#### stack : pop 알고리즘

```python
def pop():
    if len(s)==0:  # underflow (공백검사)
    	return
    else:
    	return s.pop(-1)
    
```



#### 고려사항

- 1차원 배열 사용시 구현이 용이하지만 스택의 크기를 변경하기 어렵다
- 동적 연결리스트를 사용하여 구현할 경우 
  - 메모리를 효율적으로 사용



##### Function call

- 프로그램에서의 함수 호출과 복귀에 따른 수행순서 관리
  - 가장 마지막에 호출된 함수가 가장 먼저 실행을 완료하고 복귀
  - 후입 선출
  - 함수 호출이발행하면 함수 수행에 필요한 지역변수, 매개변수, 수행후 복귀할 주소 등의 정보를 스택 프레임 (stack frame)에 저장하여 
  - 시스템 스택에 삽입
  - 함수의 실행이 끝나면 시스템 스택의 top 원소  (스택 프레임)를 삭제(pop) 하면서 프레임에 저장되어 있던 복귀 주소 확인하고 복귀
  - 함수 호출과 복귀에 따라 이 과정을 반복하여 전체 프로그램 수행이 종료되면 
  - 시스템 스택은 공백 스택이 된다



## 재귀호출

> 자기 자신을 호출하여 순환 수행되는 것



- 재귀 호출 방식을 사용해 함수를 만들면 프로그램의 크기를 줄이고 간단하게 작성
  - 종료 조건
  - 순환 구조 
- 하위 값을 이용해 상위 값을 구하는 작업 반복



## Memoization

> 중복 호출 줄이기

- 컴퓨터 프로그램을 실행할 때 이전에 계산한 값을 메모리에 저장해서 매번 다시 계산하지 않도록 한다
- 전체적인 실행속도를 빠르게 한다
- 동적 계획법 (DP, Dynamic Programming)의 핵심
- O(n)



```python
def fibo2(n):

    # memo 0, 1, 은 구현하지 않고 len(memo)가 n 보다 작을 때 구현한다
    # len(memo) 가 n 보다 크다면 이미 memo 값이 구해져 있다는 뜻
    if n >= 2 and len(memo) <= n:
        memo.append(fibo1(n-1)+fibo1(n-2))
    return memo[n]


# 현재 len(memo) = 2
memo = [1, 1]

fibo1(35)
print(memo)
```







## DP

> 동적 계획 알고리즘은 그리디 알고리즘과 같이 최적화 문제를 해결하는 알고리즘

- 입력 크기가 작은 작은 부분 문제들을 모두 해결 한 후 
- 그 해들을 이용해 큰 크기의 부분 문제를 해결한다.



### 구현 방식

- recursive (재귀) : top-down
- iterative (반복문) : bottom-up



- 재귀적 구조에 사용하는 것 보다 반복적 구조로 DP를 구현한 것이 성능면에서 효율적
- 재귀적 구조는 내부에 시스템 호출 스택을 사용하는 오버헤드가 발생하기 때문





## ✨ DFS

> 깊이 우선 탐색



- 비선형구조인 그래프 구조는 그래프로 표현된 모든 자료를 빠짐없이 검색하는 것이 중요하다



1. 깊이 우선 탐색(Depth First Search)
2. 너비 우선 탐색(Breadth First Search)



- 시작 정점의 한 방향으로 갈 수 있는 경로가 있는 곳까지

- 깊이 탐색하다가

- 더 이상 갈 곳이 없게 되면 가장 마지막 갈림길로 돌아와

  - stack

- 다른 방향의 정점으로 탐색을 반복

- 모든 정점을 방문한다.

  

##### 예) 피보나치 수열의 Call Tree

![img](https://i.stack.imgur.com/QVSdv.png)

### 과정

1. 시작 정점 v를 결정하여 방문한다
2. 정점 v에 인접한 정점 중에서
   1. 방문하지 않은 정점 w가 있으면, 
   2. 정점 v를 stack에 push하고 정점 w를 방문한다
   3. w를 v로 하여 `2` 반복한다
   4. 방문하지 않은 정점이 없으면 
   5. stack을 pop 하여 마지막에 방문한 정점을 v로 하여  `2` 반복
3. 스택이 공백이 될때까지 `2` 반복



```java
visited = []
stack = []

DFS(v):
    v // 방문
    visited[v] = true
    do{
        if(v의 인접 정점 중 방문 안한 W 찾기)
            push(v);
        while(w){
            w //방문
            visited[w] = true;
            stack.push(w);
            v=w
            // v의 인접 정점 중 방문 안 한 w 찾기
        }
        v= stack.pop()
    }while(v)
```



- visited 를 check 하는 것이 중요하다
- 목표 : 모든 정점을 방문하는 것
- 기준에 따라서 경로는 달라질 수 있다.



```
DFS_Recursive(G, v) // graph, 현재 visit 정점

visited[v] = true

for each all w in adjacency(G, v) // 인접한 모든 w
	if visited[w] != true
		DFS_Recursive(G, w)  // return 하지 않는다
```



```
Stack s
visited = []
DFS(v)
	s.push(v)
	while not isEmpty(stack): //stack이 empty 할 때까지
		v = stack.pop()
		if not(visited[v]):
			visit[v] = true
			for each w in adjacency(v):
				if not visited[w]
					stack.push(w)
```





##### 인접(Adjacency)

- 두 개의 정점에 간선이 존재하면 서로 인접해 있다고 한다.
- 완전 그래프에 속한 임의의 두 정점들은 모두 인접해 있다.



##### 인접한 노드를 어떻게 알지?

1. 인접 행렬
   1. v * v 크기의 2차원 배열을 이용해서 간선 정보 저장
   2. 행 번호와 열 번호는 그래프의 정점에 대응한다.
   3. 인접되어 있으면 1, 그렇지 않으면 0으로 표현
   4. 정점은 아주 많고 간선은 아주 적다면 불리하다.

![img](https://t1.daumcdn.net/cfile/tistory/99F7B9485B54360A21)

2. 인접 리스트

   1. 각 정점 마다 해당 정점으로 나가는 간선의 정보를 저장
   2. 정석 구현은 연결 리스트로 구현한다.
   3. 파이썬은 보다 간단하게 구현할 수 있다. (2차원 배열로)
   4. 조회만 할 때엔 유용하지만 연결 여부를 바로 알기 어렵다.

   ```
   [
   [1, 3]
   [0, 2, 3]
   [1,3]
   [0, 1, 2]
   ]
   ```

   

![img](https://t1.daumcdn.net/cfile/tistory/9992FC4B5B543F5C0F)



3. 간선의 배열



- 정점의 개수 (노드의 수)
- 간선의 수  (연결선)
  - 유향
  - 무향(쌍방향) 차이 존재 (문제에서 확인)



```python
V, E = map(int, input().split())

# V*V 크기 0으로 초기화 된 2차원 리스트를 선언한다.
adj_arr = [[0]*V for _ in range(V)]

# V개의 빈리스트를 선언하여 사용한다.
adj_list = [[] for _ in range(V)]

for i in range(E):
    A, B = map(int, input().split())

    adj_arr[A][B] = 1
    adj_arr[B][A] = 1  # 유향일 때엔 생략

    adj_list[A].append(B)
    adj_list[B].append(A)  # 유향일 때엔 생략

for i in adj_arr:
    print(*i)
```



