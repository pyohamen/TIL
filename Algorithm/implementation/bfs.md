```python
from collections import deque

def bfs(graph,start,visited):

	# 미리 visited 만듦
    bfs_visited = []

    # 수행, 방문표시
    print(start, end=' ')
    visited.append(start)
    # 시작점의 인접노드 큐에 삽입
    q = dequq()
    # 인접노드가 복수라면, extend 로 인접노드들을 q에 추가하는게 나음
    q.extend(graph[start])
    
    while queue:
    	# 큐에서 꺼냄
        v = queue.popleft()
        # 꺼냈는데 방문 안 되어 있으면
        if v not in visited:
        	# 수행
            print(v, end=' ')
            # 방문표시
            visited.append(v)
            # 큐에 인접노드 추가
            q.extend(graph[v])

graph = [
    [],
    [2,3,8],
    [1,7],
    [1,4,5],
    [3,5],
    [3,4],
    [7],
    [2,6,8],
    [1,7]
]

bfs(graph,1)
```

