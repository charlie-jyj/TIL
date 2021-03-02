# IM예제 기지국



- 집을 기준으로 탐색

```python
# 1. 기지국을 만났을 때 범위 안의 영역을 모두 X로 바꾸고 변환 후의 배열을 순회하며 H의 개수를 세기
# 2. 집을 만났을 때 반경에 기지국이 있는지 확인하고 없을 경우 answer +1
def find_station(row, col):

    delta = [
        [(0, 1), (0, -1), (1, 0), (-1, 0)],
        [(0, 2), (0, -2), (2, 0), (-2, 0)],
        [(0, 3), (0, -3), (3, 0), (-3, 0)]
    ]

    station = ['A', 'B', 'C']

    for i in range(3):
        for j in range(4):
            temp_row = row + delta[i][j][0]
            temp_col = col + delta[i][j][1]

            if 0 <= temp_row < N and 0<= temp_col < N and city[temp_row][temp_col] in station[i:]:
                return True

    return False


T = int(input())
for test_case in range(1, T + 1):

    N = int(input())
    city = [list(input()) for _ in range(N)]
    answer = 0

    for i in range(N):
        for j in range(N):
            if city[i][j] == 'H':
                if not find_station(i, j):
                    answer += 1

    print('#{} {}'.format(test_case, answer))
```





- 기지국을 기준으로 탐색
- 기지국에 따라서 반복문의 횟수를 달리하기
  - ord(city(row)(col)) - ord('A')

```python
# 1. 기지국을 만났을 때 범위 안의 영역을 모두 X로 바꾸고 변환 후의 배열을 순회하며 H의 개수를 세기
# 2. 집을 만났을 때 반경에 기지국이 있는지 확인하고 없을 경우 answer +1
def change(row, col):

    for k in range(1, ord(city[row][col])-ord('A')+2):
        # 동
        if 0 <= col + k < N and city[row][col+k] == 'H':
            city[row][col+k] = 'X'
        # 서
        if 0 <= col - k < N and city[row][col-k] == 'H':
            city[row][col-k] = 'X'
        # 남
        if 0 <= row + k < N and city[row+k][col] == 'H':
            city[row+k][col] = 'X'
        # 북
        if 0 <= row -k < N and city[row-k][col] == 'H':
            city[row-k][col] = 'X'


T = int(input())
for test_case in range(1, T + 1):

    N = int(input())
    city = [list(input()) for _ in range(N)]
    station = ['A', 'B', 'C']
    answer = 0

    for i in range(N):
        for j in range(N):
            if city[i][j] in station:
                change(i, j)

    for i in range(N):
        for j in range(N):
            if city[i][j] == 'H':
                answer += 1

    print('#{} {}'.format(test_case, answer))

```

