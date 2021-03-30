# H - index

> https://programmers.co.kr/learn/courses/30/lessons/42747



- h 를 0부터 늘려가면서 가능한지 판단
- 최댓값을 출력하는 것이기 때문에, 쭉쭉 가다가 안 되는 시점에 도달하면 (시점 - 1) 을 반환하면 됨



```python
def check(h, c):
    up = 0
    down = 0

    for n in c:
      	# 이상인 것만 세자
        if n >= h:
            up += 1
        # 그 나머지는 어차피 그 외의 나머지 논문이라 상관없음

    if up >= h:
        return True
    else:
        return False


def solution(citations):
    c = citations

    # return h - 1 이기 때문에 for 문에서 len(c) + 1 까지 해서 False 해야 return len(c) 가 됨
    for h in range(len(c) + 2):
        if check(h, c):
            continue

        else:
            if h == 0:
                return 0
            return h - 1
```

