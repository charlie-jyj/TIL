# SWEA 1208 Flatten



- 내장함수 max, min, index를 구현했다.



```python
# 최댓값의 index 를 반환하는 함수
def my_max_index(arr):
    max_value = 0
    max_idx = -1

    for idx in range(len(arr)):
        if arr[idx] > max_value:
            max_value = arr[idx]
            max_idx = idx

    return max_idx


# 최솟값의 index 를 반환하는 함수
def my_min_index(arr):
    min_value = 101
    min_idx = -1

    for idx in range(len(arr)):
        if arr[idx] < min_value:
            min_value = arr[idx]
            min_idx = idx

    return min_idx


for test_case in range(1, 11):
    # dump 횟수 제한
    dump_limit = int(input())
    # 상자들
    boxes = list(map(int, input().split()))

    # dump 횟수 제한 동안 반복한다.
    for number in range(dump_limit):

        # 최댓값, 최솟값의 index 를 return 받는다.
        max_box_index = my_max_index(boxes)
        min_box_index = my_min_index(boxes)

        # 제한 횟수 이내에 평탄화가 끝났다면 반복문을 종료한다.
        if boxes[max_box_index] - boxes[min_box_index] <= 1:
            break

        # 평탄화 작업
        boxes[max_box_index] -= 1
        boxes[min_box_index] += 1

    # limit 에 도달했다.
    print('#{} {}'.format(test_case, boxes[my_max_index(boxes)] - boxes[my_min_index(boxes)]))


```

