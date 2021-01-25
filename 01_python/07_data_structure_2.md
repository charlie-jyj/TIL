# 데이터 구조(Data Structure) 2



## 1 세트(set)

> 변경 가능하고(mutable) 순서가 없고(unordered) 순회 가능한 (iterable)



### 1.1 추가 및 삭제

#### `.add(elem)`

- elem을 set에 추가

  

#### `.update(*others)`

- add와의 차이가 있다면, 여러개를 추가한다.

- iterable한 데이터 구조를 전달해야 한다.

  ```python
  fruits = {'apple', 'grape', 'mango'}
  fruits.update(('strawberry', 'banana'))
  ```

  

#### `.remove(elem)`

- elem을 set에서 제거한다.

- 존재하지 않는 elem일 경우 에러 발생

  

#### `.discard(elem)`

- remove와의 차이: 존재하지 않은 elem이라도 에러 발생하지 않음

  

#### `.pop()`

- 임의의 원소 제거 및 반환



## 2 딕셔너리(Dictionary)

> 변경 가능하고 (mutable) 순서가 없고 (unordered) 순회 가능한 (iterable)
>
> key: value 페어(pair)의 자료구조



### 2.1 조회

#### `.get(key [,default])`

- key로 value를 가져온다.

- 존재하지 않는 key를 get해도 에러 발생하지 않는다.
- 존재하지 않는 key에 대해서 None을 반환한다, default 설정 가능하다. 



##### 중복 체크

```python
numbers = [9, 5, 6, 4, 7, 3, 2, 5, 6, 5, 7]

#0 list로 체크하기
[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

#1 중복제거 후 count로 체크
unique_numbers = list(set(numbers))

for number in unique_numbers:
    numbers.count(number)
    
#2 dictionary의 get 메소드 사용
result = {}
for number in numbers:
    result[number] = result.get(number, 0) + 1
    
result
```





### 2.2 추가 및 삭제

#### `.pop(key [,default])`

- key가 딕셔너리에 존재한다면 제거하고 그 값을 return

- key가 존재하지 않는다면 default를 반환하지만 default가 없을 경우  KeyError 에러발생

  

#### `.update()`

- 값을 제공하는 key, value로 덮어쓴다.

```python
fruits ={'a':'apple', 'b':'banana', 'c':'carrot'}

fruits.update({'g':'grape'})
fruits.update(o='orange')
```





### 2.3 딕셔너리 순회

- for 문으로 순회
  - 기본적으로 key (key를 통해 value를 알 수 있기 때문)
  - keys()
  - values()
  - items()

```python
#1
for key in dict:
    print(dict[key])
    
#2
for key in dict.keys():
    print(dict[key])

#3
for value in dict.values():
    print(value)
    
#4
for key, value in dict.items():
    print(key, value)
 
```



### Dictionary comprehension

- {키: 값  `for` 요소 `in` iterable}
- dict({키: 값  `for` 요소 `in` iterable})
- 잘 쓰지 않는다.



### Dictionary comprehension + 조건

- {키: 값 `for` 요소 `in`  iterable `if` 조건식}
- {키: 값 `if` 조건식 `else` 값`for` 요소 `in`  iterable }

