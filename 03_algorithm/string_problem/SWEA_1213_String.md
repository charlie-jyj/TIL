# SWEA 1213 String



- brute force

```python
for test_case in range(1, 10 + 1):
    tc = int(input())
    pattern = input()  # 찾을 문자열
    text = input()  # 검색할 문자열

    pt = 0  # text 인덱스
    pp = 0  # pattern 인덱스
    match_count = 0  # pattern 을 찾은 횟수

    # 검색할 문자열을 처음부터 끝까지 1번 검색한다.
    while pt != len(text):

        # 값 비교해서 같다면 인덱스를 1 증가시켜 다음 값 확인
        if text[pt] == pattern[pp]:
            pt += 1
            pp += 1
        # 값이 다르다면 pt는 시작위치 + 1로 옮기고 pp는 0으로 초기화
        else:
            pt = pt - pp + 1
            pp = 0

        # 패턴을 찾았다면 count 를 1 증가 시키고 pp 다시 초기화(한 번 찾고 끝나는 게 아니기 때문)
        if pp == len(pattern):
            match_count += 1
            pp = 0

    print('#{} {}'.format(tc, match_count))

```



- slicing
- 이 쪽이 좀더 빠르다.

```python
for test_case in range(1, 10 + 1):
    tc = int(input())
    pattern = input()  # 찾을 문자열
    text = input()  # 검색할 문자열

    match_count = 0  # pattern 을 찾은 횟수

    # 구간만큼 text 를 slicing 했을 때 pattern 과 같다면 count + 1 한다.
    for i in range(len(text)-len(pattern)+1):
        if text[i:i+len(pattern)] == pattern:
            match_count += 1

    print('#{} {}'.format(tc, match_count))

```

