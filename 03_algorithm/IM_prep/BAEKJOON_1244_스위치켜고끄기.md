# 1241 스위치 켜고 끄기



- 비트 연산자를 이용했다.



```python
N = int(input())
switch = list(map(int, input().split()))
M = int(input())
student = [list(map(int, input().split())) for _ in range(M)]

for i in range(M):
    gender = student[i][0]
    number = student[i][1]

    for j in range(N):
        if gender == 1:
            if (j+1) % number == 0:
                switch[j] = switch[j]^1

        elif gender == 2:
            if j+1 == number:

                delta = 1
                while True:
                    if 0 <= j + delta < N and 0 <= j - delta < N:
                        if switch[j+delta] != switch[j-delta]:
                            delta -= 1
                            break
                        else:
                            delta += 1
                    else:
                        delta -= 1
                        break

                for k in range(j-delta, j+delta+1):
                    switch[k] = switch[k]^1

idx = -1
while idx < N:
    temp = ''
    for j in range(20):
        idx += 1
        if idx < N:
            temp += str(switch[idx])
        else:
            break
    print(' '.join(temp))
```

