## DFS(Depth-First Search)

- 깊이 우선 탐색 -> 깊은 부분을 우선적으로 탐색하는 알고리즘

- 스택자료구조(혹은 재귀 함수)를 이용

  1. 탐색 시작 노드를 스택에 삽입하고 방문
  2. 스택의 최상단 노드에 방문하지 않은 인접한 노드가 하나라도 있으면 그 노드를 스택에 넣고 처리. 방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼냄
  3. 더 이상 2번의 과정을 수행할 수 없을 때까지 반복

  ```python
  #DFS 메소드 정의
  def dfs(graph, v, visited):
      #현재 노드를 반문 처리
      visited[v] = True
      print(v, end=' ')
      for i in graph[v]:
          if not visited[i]:
              dfs(graph, i , visited)
  #각 노드가 연결된 정보를 표현 (2차원 리스트)
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
  #각 노드가 방문된 정보를 표현(1차원 리스트)
  visited = [False] *9
  #정의된 DFS 함수 호출
  dfs(graph, 1, visited)
              
  결괏값: 1 2 7 6 8 3 4 5
  ```



## BFS (Breadth-First search)

- 너비 우선 탐색 -> 가까운 노드부터 우선적으로 탐색하는 알고리즘
- 큐 자료구조를 이용
  1. 탐색 시작 노드를 큐에 삽입하고 방문
  2. 큐에서 노드를 꺼낸 뒤에 해당 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 방문 처리
  3. 더 이상 2번의 과정을 수행할 수 없을 때까지 반복

```python
from collections import deque

#BFS 메소드 정의
def bfs(graph, start, visited):
    #큐(queue) 구현을 위해 deque 라이브러리 사용
    queue = deque([start])
    #현재 노드를 방문 처리
    visited[start] = True
    #큐가 빌 때까지 바놉ㄱ
    while queue:
        #큐에서 하나의 원소를 뽑아 출력하기
        v = queue.popleft()
        print(v, end= ' ')
        #아직 방문하지 않은 인접한 원소들을 큐에 삽입
        for i in graph[v]:
            if not visted[i]:
                queue.append(i)
                visited[i] = True
#각 노드가 연결된 정보를 표현 (2차원 리스트)
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
#각 노드가 방문된 정보를 표현(1차원 리스트)
visited = [False] *9
#정의된 DFS 함수 호출
dfs(graph, 1, visited)

```

