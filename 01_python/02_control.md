# 제어문(Control Statement)

>특정 상황에 따라 코드를 선택적으로 실행(분기)하거나 동일한 코드를 계속해서 실행해야 할 때
>
>코드 실행의 순차적인 흐름을 제어



## if

> 참 거짓을 판단할 수 있는 조건과 함께 쓰인다.

```python
if a > 0:
	print('양수')  # indent 주의
else:
	print('음수')
```



### 조건 표현식(Conditional Expression)

> 삼항연산자
>
> if,else로만 이루어진 조건식일때

- true_value if <조건식> else false_value

  ```
  value = num if num >= 0 else -num
  ```

  



## for

> for x in sequence

- for <임시변수> in <순회 가능한 데이터(iterable)> :

  ​		<코드 블럭>

- sequence 는 순회 가능한 데이터 (string 포함)

- for 문 내부에서 임시변수에 다른 값을 할당해도 반복문 횟수에 영향을 주지 않는다.

  ```python
  for index in range(5):
  	index = 3
  	print('출력!')  # 5번 출력된다.
  ```

  

- for i in range(10): 0123456789 (i의 값이 바뀐다)

- list 순회하기

  - range와 index 사용하기
  - enumerate()
    - enumerate(iterable, start=0)
    - iterable은 시퀀스, 이터레이터를 지원하는 다른 객체
    - (index, value)의 tuple을 반환한다.

  ```python
  sweets = ['choco', 'candy', 'caramel', 'jelly']
  #1
  for idx in range(len(sweets)):
  	print(sweets[idx])
  
  #2
  for sweet in sweets:
  	print(sweet)
      
  #3
  for sweet in enumerate(sweets):
      print(sweet)
  ```
  
  



## while

> break

##### while을 종료시키는 방법

1. while 조건식
2. break



- while <조건식>:

  ​	<코드 블럭>

- while True 는 무한 반복되므로 break 필요하다.



### 반복 제어

1. break
   - 반복문 종료

2. continue
   - continue 이후의 코드를 뛰어넘고 반복을 진행한다.

3. for-else
   - for문의 경우 조건이 거짓이 될 경우
   - while의 경우 종료될 때 실행
   - break로 종료되었을 때엔 실행되지 않음
4. pass
   - 자리를 채우는 placeholder





