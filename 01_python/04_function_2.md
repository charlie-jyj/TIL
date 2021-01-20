# function 2



## 함수와 Scope

> 함수는 코드 내부에 scope를 생성하고 함수로 생성된 공간을 local scope라고 한다.

##### 스코프는 함수에서 생긴다. if/for같은 제어문은 영향을 받지 않는다.



###  전역 스코프(global scope)

- 전역 변수 (global variable)

- 지역스코프에서 선언된 지역변수를 알지 못한다.

- 알고리즘  문제 풀 때가 아니고서야 전역 변수 잘 쓰지 않는다.

  

### 지역 스코프(local scope)

- 지역 변수 (local variable)
- 전역 변수와 동일한 이름으로 지역변수를 선언할 경우, 지역변수가 우선되고 메소드 종료 후 삭제된다.



### 이름 검색(resolution) 규칙 LEGB

1. local scope : 정의된 함수

2. enclosed scope : 상위 함수

3. global scope : 함수 밖의 변수 혹은 import된 모듈

4. built -in scope : 파이썬 내장 함수 혹은 필드



### 변수의 수명주기

- 빌트인 스코프(built-in scope) : 파이썬이 실행된 이후부터 영원히
- 전역 스코프 (global scope): 모듈이 호출된 시점 이후/이름 선언된 이후부터 인터프리터가 끝날 때까지
- 지역 스코프(local scope) : 함수가 호출되며 생성, 함수가 종료(return) 되며 끝



cf) 인터프리터란, 코드를 해석해 컴퓨터에게 일을 시키는 python의 인터프리터를 의미한다.



## 재귀 함수(recursive function)

> 함수 내부에서 자기 자신을 호출하는 함수

- 바닥(base case)을 if 조건으로 구현하여 바닥을 찍으면 return이 반복된다.

- base case란 범위가 줄어들어 반복되지 않는 최종 단계

- 팩토리얼 계산

- 변수 사용을 줄일 수 있다. 

- RecursionError   : maximum recursion depth 3000

- 속도 자체는 반복문이 빠르다.

  ```python
  
  def facto(number):
      
      if number==1:  # 바닥 
          return 1
      else:
          number*facto(number)
  ```

  



