# 데이터 구조(Data Structure) 2



## 1 세트(set)

> 변경 가능하고(mutable) 순서가 없고(unordered) 순회 가능한 (iterable)



### 1.1 추가 및 삭제

#### .add(elem)

#### .update(*others)

#### .remove(elem)

#### .discard(elem)

- remove와의 차이: 존재하지 않은 elem이라도 에러 발생하지 않음

#### .pop()

- 임의의 원소 제거 및 반환



## 2 딕셔너리(Dictionary)

> 변경 가능하고 (mutable) 순서가 없고 (unordered) 순회 가능한 (iterable)
>
> key: value 페어(pair)의 자료구조



### 2.1 조회

#### .get(key [,default])



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
    if result.get(num):
        result[number] += 1
    else:
        result[number] = 1
result
```





### 2.2 추가 및 삭제



#### .pop(key [,default])

- key가 존재하지 않는데 default가 없다? 에러 발생

#### .update()



### 2.3 딕셔너리 순회



### Dictionary comprehension



### Dictionary comprehension + 조건

