# SWEA 1909 Sum



```python
T = 10
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    nth = int(input())
    arr = []
    for i in range(100):
        arr.append(list(map(int, input().split())))

    # 갱신할 최댓값
    max_sum = 0

    # 왼쪽 대각선
    left = 0
    # 오른쪽 대각선
    right = 0

    for i in range(100):
        # 행
        row = 0
        # 열
        col = 0

        # 행과 열의 합
        for j in range(100):
            row += arr[i][j]
            col += arr[j][i]

            # 왼쪽 대각선은 i와 j가 같을 때
            if i == j:
                left += arr[i][j]

            # 오른쪽 대각선은 i+j = 99 일 때
            if i + j == 99:
                right += arr[i][j]

        # 행과 열의 합은 각각 100개 나온다.
        if max_sum < row:
            max_sum = row
        if max_sum < col:
            max_sum = col

    # 대각선의 합은 왼쪽, 오른쪽 2개
    if max_sum < left:
        max_sum = left
    if max_sum < right:
        max_sum = right

    print('#{} {}'.format(nth, max_sum))



```

