# 큐 (Queue)



##### 주의

- 배열로 크기 지정 후 사용했을 때에는 시간초과가 나지 않지만
- 빈 리스트 선언 후 사용했을 때 시간 초과가 나기도 한다
  - 내부적으로 자원 이동이 많이 이루어지기 때문에
- 라이브러리 deque 사용 가능



## 큐

> 삽입과 삭제의 위치가 제한적인 자료구조
>
> 선입선출구조 (FIFO: First In First Out)
>
> 큐의 뒤에서 삽입, 큐의 앞에서 삭제



### 구조와 기본연산



#### 구조

- 선입선출
- Front
  - 저장된 원소 중 첫 번째 원소
  - 💎마지막에 꺼내진 위치
- Rear
  - 저장된 원소 중 마지막 원소



#### 기본 연산

- enQueue(item)
  - 큐의 뒤(rear)에 원소를 삽입
- deQueue()
  - 큐의 앞(front)에서 원소를 삭제하고 반환
  - front += 1
- createQueue()
  - 공백 상태의 큐를 생성
- isEmpty()
  - 큐가 공백상태인지 확인하는 연산
  - 길이가 0 
  - front와 rear가 같은 값을 가진다
  - while front != rear
- isFull()
  - 큐가 포화상태인지 확인하는 연산
- Qpeek()
  - 큐의 앞쪽(front)에서 원소를 삭제 없이 반환
  - Q[front + 1]



```python
# createQueue()
queue = [0]*N
front = rear = -1

# enQueue(A) 삽입할 때는 rear가 움직인다.
rear += 1
queue[rear] = A
rear += 1
queue[rear] = B

# deQueue 삭제할 때는 front가 움직인다.
front += 1
queue[front]

# enQueue
rear += 1
queue[rear] = C

# deQueue
front += 1
queue[front]

front += 1
queue[front]

if front == rear:
    print('공백')
```



### 큐의 구현

- 선형 큐
  - 1차원 배열을 이용한 큐
    - 큐의 크기는 배열의 크기
    - front/ rear
  - 상태 표현
    - 초기 상태 : front = rear = -1
    - 공백 상태 : front = rear
    - 포화 상태 : rear = n-1



#### enQueue(item)

```python
def enQueue(item):
	global rear
	if isFull():
		print('queue is full')
    else:
    	rear += 1
    	queue[rear] = item
```



#### deQueue()

```python
def deQueue():
    global front
    if isEmpty():
        print('queue is empty')
    else:
        front += 1
        return queue[front]
```



#### isEmpty(), isFull()

```python
def isEmpty():
    return front == rear  # bool 을 반환한다

def isFull():
    return rear == len(queue) - 1
```



#### Qpeek()

```python
def Qpeek():
    if isEmpty():
        print('queue is empty')
    else:
        return queue[front+1]
```



#### 선형 큐 이용 시 문제점

- 잘못된 포화상태 인식

1. 원소 삽입 삭제를 계속할 경우, 배열 앞 부분에 활용할 수 있는 공간이 있지만
2. rear = n-1 포화 상태로 인식하여 더 이상 삽입하지 않는다



- 해결 방법 1
  - 연산이 이루어질 때마다 저장된 원소들을 배열의 앞부분으로 모두 이동
  - 원소 이동에 많은 시간이 걸린다
- 해결 방법 2
  - 1차원 배열 사용하되, 논리적으로 배열의 처음과 끝이 연결되어 
  - 원형 형태의 큐를 이룬다고 가정하고 사용



### 원형 큐의 구조

- 초기 공백 상태
  - front = rear = 0
- index 의 순환
  - front와 rear의 위치가 배열의 마지막 인덱스 n-1 가리킨 후 논리적 순환을 이루어
  - 배열의 처음 인덱스인 0으로 이동한다 
  - 나머지 연산자 mod 이용 (%)
- front 변수
  - 공백 상태와 포화상태를 쉽게 구분하기 위해 front 자리는 사용하지 않고 빈 자리로 둔다
  - 내가 원하는 값의 개수(N) 보다 1 큰 (N+1) 로 크기 선언하여 사용한다.



|         | 삽입 위치           | 삭제 위치             |
| ------- | ------------------- | --------------------- |
| 선형 큐 | rear = rear + 1     | front = front + 1     |
| 원형 큐 | rear = (rear+1) % n | front = (front+1)_% n |



#### 연산 과정

```python
# createQueue
queue = [0]*N
front = rear = 0

# enQueue(A)
rear = (rear+1) % N
queue[rear] = A

rear = (rear+1) % N
queue[rear] = B

# deQueue()
front = (front+1) % N
return queue[front]

# enQueue(C)
rear = (rear+1) % N
queue[rear] = C

rear = (rear+1) % N
queue[rear] = D

```



### 원형 큐의 구현

#### isEmpty(), isFull()

```python
def isEmpty():  # 선형 큐와 동일
	return front == rear

# rear가 front 바로 뒤에 있을 때
def isFull():
	return (rear+1)%len(queue) == front
```



#### enQueue(item)

```python
def enQueue(item):
    global rear
    
    if isFull():
        print('queue is full')
    else:
        rear = (rear+1)%len(queue)
        queue[rear] = item
```



#### deQueue(), delete()

```python
def deQueue():
    global front
    if isEmpty():
        print('queue is empty')
    else:
        front = (front+1)%len(queue)
        return queue[front]
```



### 연결 큐의 구조

- 단순 연결 리스트(Linked List)를 이용한 큐
  - 큐의 원소 : 단순 연결 리스트의 노드
  - 큐의 원소 순서 
    - 노드의 연결 순서, 링크로 연결
    - 공간 활용도가 좋다
  - front
  - rear
- 초기 상태
  - front = rear = None
- 공백 상태
  - front = rear = None



## 우선순위 큐

> 우선순위를 가진 항목들을 저장하는 큐
>
> FIFO 가 아니라 우선 순위가 높은 순서대로 먼저 나간다



- 적용 분야
  - 시뮬레이션
  - 네트워크 트래픽 제어
  - 운영체제의 테스크 스케줄링



#### 우선순위 큐의 구현

- 배열
  - 원소를 삽입하는 과정에서 우선 순위를 비교하여 적절한 위치에 삽입
  - 가장 앞에 최고 우선 순위 원소가 위치
  - 원소의 재배치로 인한 시간, 메모리 낭비 
- 리스트
- heap



#### 우선순위 큐의 기본 연산

- enQueue

- deQueue

  





## 🧨 BFS

> 탐색 시작점에 인접한 정점들을 먼저 모두 차례로 방문한 후에 
>
> 방문했던 정점을 시작점으로 하여 다시 인접한 정점들을 차례로 방문한다.
>
> 인접한 정점들 탐색한 후 차례로 다시 너비우선탐색을 진행 하므로 
>
> 선입선출 형태의 자료구조 큐를 활용



- 그래프 탐색하는 방법 2 가지
  1. DFS (깊이우선탐색)
  2. BFS (너비우선탐색)



- BFS (Breadth First Search)

![img](https://cdn.shortpixel.ai/client/q_glossy,ret_img/https://vivadifferences.com/wp-content/uploads/2019/10/DFS-VS-BFS.png)



```python
def BFS(G, v):  # G 그래프, v 탐색 시작점
    
	visited = [0]*n  # 정점의 개수
	queue = []  # 큐 생성
	queue.append(v)  # 시작점 큐에 삽입
    
    visited[v] = True # 시작점 방문 체크
    
	while queue:  # 큐가 비어있지 않은 경우
		t = queue.pop(0)  # 큐의 첫 번째 원소 반환
			
		for i in G[t]:  # t와 연결된 모든 선에 대해
			if not visited[i]:  # 방문되지 않은 곳이라면
				queue.append(i)  # 큐에 삽입
                visited[i] = True  # append 하면서 동시에 방문 체크 (중복으로 큐에 넣는 것 방지)

```



- 방문 여부 뿐만 아니라 거리에 대한 정보를 담을 수도 있다.

  1. 큐에 넣을 때 튜플로 시작점에서부터의 거리를 담을 수도 있지만

  2. visited 방문 배열에 (부모노드 값+ 1 )거리를 담아  '시작점에서부터의 거리' 를 체크할 수도 있다.

  3. queue 사이즈로 묶어 while 문을 반복하면서 형제를 다루면 변수 하나로 거리를 알 수 있다.

  

```python
while queue:
	size = len(queue)
	
	# 거리가 같은 노드끼리 묶어서 형제들을 추출할 수 있다.
	for i in ragne(size):
		tmp += queue.pop(0)
```



- 미로 탈출 여부 + 목적지 까지의 거리 측정 가능
- 거리를 판단할 수 있다 BFS
- 방문 체크 하지 않으면 while 문을 벗어날 수 없다
- 최단 시간, 최단 거리 => BFS 를 사용해보자







## 큐의 활용 : 버퍼

> 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리의 영역



- 일반적으로 입출력 및 네트워크와 관련
- 순서대로 입력/출력/전달 되어야 하므로 FIFO 방식인 큐가 활용된다