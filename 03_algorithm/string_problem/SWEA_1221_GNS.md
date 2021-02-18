# SWEA 1221 GNS



- 숫자판을 순회하며 내부에서 원본을 순회하여 일치하는 문자를 리스트에 추가한다.

```python
T = int(input())
for test_case in range(1, T + 1):
    TC, L = map(str, input().split())  # 테스트케이스 번호, 테스트 케이스 길이
    length = int(L)
    text = input().split()  # 테스트 케이스
    order = ['ZRO', 'ONE', 'TWO', 'THR', 'FOR', 'FIV', 'SIX', 'SVN', 'EGT', 'NIN']
    result = []

    # order 를 순회하며 text 의 값과 order 값이 일치하면 리스트에 추가한다.
    # 순서대로 추가된다 ZRO ONE TWO...
    for i in range(len(order)):
        for j in range(length):
            if order[i] == text[j]:
                result.append(order[i])

    print(TC)
    print(*result)
```



- 출현한 문자의 수를 counting 해서 그 수 만큼 문자열에 추가한다.

```python
T = int(input())
for test_case in range(1, T + 1):
    TC, L = map(str, input().split())  # 테스트케이스 번호, 테스트 케이스 길이
    length = int(L)
    text = input().split()
    order = ['ZRO', 'ONE', 'TWO', 'THR', 'FOR', 'FIV', 'SIX', 'SVN', 'EGT', 'NIN']

    counting = [0] * 10
    result = ''

    for i in range(len(text)):
        if text[i] == 'ZRO':
            counting[0] += 1
        elif text[i] == 'ONE':
            counting[1] += 1
        elif text[i] == 'TWO':
            counting[2] += 1
        elif text[i] == 'THR':
            counting[3] += 1
        elif text[i] == 'FOR':
            counting[4] += 1
        elif text[i] == 'FIV':
            counting[5] += 1
        elif text[i] == 'SIX':
            counting[6] += 1
        elif text[i] == 'SVN':
            counting[7] += 1
        elif text[i] == 'EGT':
            counting[8] += 1
        else:
            counting[9] += 1

    for i in range(len(order)):
        for j in range(counting[i]):
            result += order[i]+' '

    print(TC)
    print(result)
```



- 외계인 숫자를 int 숫자로 변환하여 정렬하고 다시 변환하는 방법도 있다.