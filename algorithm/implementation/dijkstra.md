

> 노드별 distance 리스트

> 노드 별 연결 노드 정보

> 수행했는지 Visited 리스트에 쌓아가며 수행

# 흐름

1. 출발노드 설정

2. 최단 거리 Table 을 초기화

   ```python
   distance = [0, INF, INF,,,]
   ```

3. 방문하지 않은 노드 중 최단 거리가 가장 짧은 노드를 선택

   > 출발노드로부터 매 번 가장 짧은 거리를 우선적으로 선택해왔기 때문에, 방문하지 않은 노드가 최단 거리가 된다.

4. 해당 노드를 거쳐 다른 노드로 가는 비용을 계산해 최단 거리 테이블을 갱신

5. 3, 4 번 과정 반복



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



# heapq 를 이용

```python
import heapq
import sys
input = sys.stdin.readline
INF = int(1e9)

# 노드의 개수, 간선의 개수 입력받기
n, m = map(int, input().split())
# 시작 노드번호를 입력받기
start = int(input())
# 각 노드에 연결되어 있는 노드에 대한 정보를 담는 리스트를 만들기
graph = [[] for i in range(n + 1)]
# 최단 거리 테이블 초기화
distance = [INF] * (n + 1)

# 간선 정보 입력받기
for _ in range(m):
  a, b, c = map(int, input().split())
  graph[a].append((b, c))
  
def dijkstra(start):
  q = []
  # 시작 노드로 가기 위한 최단 경로는 0 으로 설정하여, 큐에 삽입
  heapq.heappush(q, (0, start))
  distance[start] = 0
  while q:
    dist, now = heapq.heappop(q)
    # 현재 노드가 이미 처리된 적이 있어서 이미 최단거리 테이블에 더 작은 값이 있다면 무시
    if distance[now] < dist:
      continue
    # 인접 노드 확인
    for dis, node in graph[now]:
      cost = dist + dis
      if cost < distance[node]:
        distance[node] = cost
        heapq.heappush(q, (cost, node))
```

