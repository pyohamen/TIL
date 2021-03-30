```python
def dfs(graph, v, visited):

    # 현재 노드수행, 방문처리
    print(v, end=' ')
    visited[v] = True

    # 인접노드 탐색
    for i in graph[v]:
    	# 방문 안되어있으면
        if not visited[i]:
        	# 재귀
            dfs(graph,i,visited)

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

visited = [False]*9

# 1 은 현재노드
dfs(graph,1,visited)
```

