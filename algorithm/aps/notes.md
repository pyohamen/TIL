# APS

- 조건문은 꼭 else: 도 고려하자. if 문 일때만 고려하는 흐름이 computitational thinking 에 맞지만, 놓칠 수 있다.

  - 퇴사 다이나믹 에서 else: 를 안 해도 된다고 착각함
  
- 우선으로 수행해야하는 것을 **그려서** 파악하여 구현하자. 문제 순서가 아니라

  - 공통되는 조건을 파악하자.
  - 그려놓으면 뭐부터 지워가야 우선수행을 알기 쉽다

- 코테에서 문제 해석에 많은 시간이 들어서, 그냥 나올 수 있는 모든 경우의 수를 나눠 각각 푸는게 나을 것 같다. 모든 가능성을 시험하며 한번에 타파하는 알고리즘을 주어진 시간내에 하는게 어렵다

- ㄹㅇ.. 문장에 정답 조건이 있다..

- 구현은 종이에

- aps 를 할 때 생각한 자료구조가 구현할 때 다른 자료구조가 편할 수 있다. aps 하면서 구현가능성도 동시에 깊이 생각하자.

- 변수설정을 하고, 문제를 한문장 한문장 읽어가면서 변수를 비교하자.

  - Ex) 뱀 문제에서 문제에 사과가 없어진다고 명시해있는 것을 보고, 코드에서 사과를 remove 해줘야 한다는 것을 알 수 있다.
  
- 문제가 많이 복잡할 시

  - ```python
    while True:
    		원하는 지점 도달시
    				수행
    				exit()
    ```

- 변수설정을 적극적으로 활용하자. 과도한 인덱싱 ㄴㄴ

- 내가 필수적으로 수행해야할 것만 구현하자. 계산은 컴퓨터가

- 구현을 해나가면서 중간 디버깅을 하자

- 최댓값, 최솟값 업데이트 시

  - ```python
    min_answer = int(1e9)
    max_answer = -int(1e9)
    ```

- 자료구조가 str 일 때 더 편할 수 있다.

- string[0] 은 " 이다.



# For loop

- In list 를 잘 활용하자 => range over 가 일어나지 않는다.

  - ```
    for value in list:
    ```



- 반복문 range 를 활용하자

  - ```python
    for i in range(a,b,c):
    
    # a 부터 시작되며
    # b 전까지 해당되고
    # c 단위로 늘어난다
    ```



- split 된 정보들을 입력받는 동시에 자료를 만들자

  - ```python
    graph = [[] for _ in range(n+1)]
    for i in range(m):
        a,b = map(int,input().split())
        graph[a].append(b)
    ```



- for 문에서 List 를 편집할 때 주의 !

  - ```python
    for v in list:
    	list.append(v + n)
        
    # 위처럼 하게 되면 반복문안에서 list 가 편집되기 때문에 오류가 생긴다
    
    length = len(list)
        for i in range(length):
            list.append(list[i] + n)
            
    # 번거롭더라도 이런식으로 구현하자
    ```



- for 문 안에서 사용한 변수는 해당 for 문 위에서 초기화



# List - Based

- 시뮬레이션을 할 때, 2차원 배열에서 위치가 계속 변한다면, [x, y] 형태의 element 를 갖는 1차원 리스트로 만들자. 

  - => 2차원 배열상의 정보가 겹치거나 인덱스 범위 오류를 막을 수 있다.

  - ```python
    el_locs = [[x, y], [x, y], [x, y]...]
    ```

  - ```python
    # 해당 위치가 v_locs 안에 있는지 없는지
    if [x, y] in el_locs:
    ```



- Queue 나 Stack 에 인접노드를 push 할 때 노드 자체에 정보를 담아 기존 노드 기반으로 정보를 부여하여 인접노드를 push 해줄 수 있다.

  - ```python
    # ex)
    data = []
    for y in range(n):
        for x in range(n):
            if arr[y][x]:
                data.append((arr[y][x],0,y,x))
    
    # 그 이전 노드로 인해 진행된 인접노드를 큐에 삽입할 때 기존 노드의 시간 +1 을 해주는 개념            
    while q:
        virus,time, y,x = q.popleft()
        if time == s:
            break
        for i in range(4):
            ny = y + dy[i]
            nx = x + dx[i]
    
            if 0 <= ny < n and 0 <= nx < n:
                if not arr[ny][nx]:
                    arr[ny][nx] = virus
                    q.append((virus, time+1, ny,nx))
    ```

    

- Permutation / Combination

  - ```python
    from itertools import permutations
    from itertools import combinations
    
    a = []
    b = []
    items= [1,2,3,4]
    
    list(combinations(items, m))
    list(permutations(items, m))
    ```

- Least common multiple

  - ```python
    Arr = list(map(int,list(input().split())))
    
    n = 1
    while n%Arr[0] or n%Arr[1] or n%Arr[2]:
        n += 1
    
    print(n)
    ```

    

# 2 - dimensional array

- 2차원 배열을 수정해야할 때는 기존의 배열을 수정하지 말고, 같은 크기의 빈 배열을 만들어 모든 인덱스에 적절한 값을 할당한 후 교체하는 방식을 따르자

- 90 도 회전

  - ```python
    list(zip(*arr[::-1]))
    ```

- split 된 정보를 입력받을 때

  - ```python
    graph = [[] for _ in range(n+1)]
    for i in range(m):
        a,b = map(int,input().split())
        graph[a].append(b)
    
    ```

- 기본적으로 nx, ny 의 조건문을 할 때는 인덱스 범위 먼저 검토해야한다.

  ```python
   if 0 > nx or r <= nx or 0 > ny or c <= ny or a[nx][ny] == 1:
          d = (d + 1) % 4
          nx = x + dx[d]
          ny = y + dy[d]
  
  만약 조건문에서 a[nx][ny] 를 먼저 수행한다면 인덱스 오류가 나지만,
  앞에서 범위가 벗어난 것이 하나라도 발견되면 or 문이기때문에 그냥 넘어갈 수 있다.
  ```

- 회전

  ```python
  list(zip(*arr[::-1]))
  ```

  

# Recursion

- 함수내에서 필요한 변수를 생각하고 인자 설정을 하자



# Hash

- 딕셔너리 구현

  ```python
  # key 를 숫자 순서대로 할 때
  
  dic = dict()
  lst = [chr(i) for i in range(ord('A'), ord('Z') + 1)] # Value 로 가질 값들의 리스트 구현
  
  for idx, char in enumerate(lst):
      dic[char] = idx + 1 # 여기서 순서 바꿔주면 키와 밸류가 바뀐다
  ```

  