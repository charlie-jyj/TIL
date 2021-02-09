# SWEA 4828 min_max

- 내장함수를 사용하지 않는다.

```python
T = int(input())

for test_case in range(1, T + 1):
    case_length = int(input())
    numbers = list(map(int, input().split()))

    answer = 0

    # numbers 를 정렬하자
    # bubble sort
    for i in range(len(numbers)-1, 0, -1):
        for j in range(0, i):
            if numbers[j] > numbers[j+1]:
                numbers[j], numbers[j+1] = numbers[j+1], numbers[j]

    answer = numbers[-1] - numbers[0]

    print('#{} {}'.format(test_case, answer))
```

