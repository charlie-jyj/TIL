# 입력받기



```
3
9
7 4 2 0 0 6 0 7 0
9
7 4 2 0 0 6 7 7 0
20
52 56 38 77 43 31 11 87 68 64 88 76 56 59 46 57 75 85 65 53
```



1. 복사+ 붙여넣기

```python
for tc in range(1, int(input())+1):
    N = int(input())
    box = list(map(int, input().split()))

    ans = 1
    print("#{} 길이의 배열: {}".format(N, box))
```



2. 파일 열기

```python
import sys
sys.stdin = open('input.txt', 'r')
```

- stdin = standard input
- built in 함수 open()
- 'r'은 read mode를 뜻한다.