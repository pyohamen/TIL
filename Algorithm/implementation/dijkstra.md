> 노드별 distance 리스트

> 노드 별 연결 노드 정보

> 수행했는지 Visited 리스트에 쌓아가며 수행

# 흐름

1. 시작노드 수행
2. 매 번 제일 거리가 짧은 노드부터 수행
3. 거리가 더 짧다면 distance 업데이트



### 간단한 구현, 속도 느림

```python
import sys

INF = int(1e9)

# 노드의 개수, 간선의 개
n, m = map(int,sys.stdin.readline().split())
# 시작 노드 번호 입력
start = int(input())
# 각 노드에 연결되어 있는 노드에 대한 전보를 담는 리스트
graph = [[] for i in range(n + 1)]
# 방문 리스트
visited = [False] * (n + 1)
# 최단 거리 테이블 모두 무한으로 초기화
distance = [INF] * (n + 1)
# 모든 간선 정보 입력받기
for _ in range(m):
    # a 노드에서 b 노드로 가는 비용이 c
    a, b, c = map(int,input().split())
    graph[a].append((b,c))

def get_smallest_node():
    min_value = INF
    index = 0
    for i in range(1, n+1):
        if distance[i] < min_value and not visited[i]:
            min_value = distance[i]
            index = i
    return index

def dijkstra(start):
    distance[start] = 0
    visited[start] = True

    for node_info in graph[start]:
        distance[node_info[0]] = node_info[1]

    for i in range(n-1):

        now = get_smallest_node()
        visited[now] = True

        for node_info in graph[now]:
            cost = distance[now] + node_info[1]
            if cost < distance[node_info[0]]:
                distance[node_info[0]] = cost
```

