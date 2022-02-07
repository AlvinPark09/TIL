## 서로소 집합(disjoint Sets) 을 판단하기 위한 유니온 파인드(union find)

- 공통 원소가 없는 두 집합

- 두 종류의 연산을 지원

  - 합집합(union): 두 개의 원소가 포함된 집합을 하나의 집합으로 합치는 연산
  - 찾기(find): 특정한 원소가 속한 집합이 어떤 집합인지 알려주는 연산

- 서로소 집합 자료구조는 합치기 찾기(union find) 자료구조라고 불리움

- steps

  1. 합집합(union) 연산을 확인하여 서로 연결된 두 노드 A, B를 확인
     1) A와 B의 루트 노트  A', B'를 각각 찾습니다
     2) A'를 B'의 부모 노드로 설정
  2. 모든 합집합 연산을 처리할 때까지 1번 과정 반복

  ```python
  #특정 원소가 속한 집합을 찾기
  def find_parent(parent, x):
      #루트 노드를 찾을 때까지 재귀 호출
      if parent[x] != x:
          return find_parent(parent, parent[x])
      return x
  ############################################################
  #두 원소가 속한 집합을 합치기
  def union_parent(parent, a, b):
      a = find_parent(parent, a)
      b = find_parent(parent, b)
      if a < b:
          parent[b] = a
  	else:
          parent[a] = b
  
  #노드의 개수와 간선(union 연산)의 개수 입력 받기
  v, e = map(int, input().split())
  parent = [0] * (v +1) #부모 테이블 초기화하기
  
  #부모 테이블상에서, 부모를 자기 자신으로 초기화
  for i in range(1, v+1):
      parent[i] = i
      
  #union 연산을 각각 수행
  for i in range(e):
      a, b = map(int, input().split())
      union_parent(parent, a, b)
      
  #각 원소가 속한 집합 출력하기
  print('각 원소가 속한 집합: ', end=' ')
  for i in range(1, v+1):
      print(find_parent(parent, i ), end=' ')
      
  print()
  
  #부모 테이블 내용 출력하기
  print('부모 테이블: ', end = '')
  for i in range(1, v+1):
      print(parent[i], end= ' ')

- 문제점:
  - 합집합 연산이 편향되게 이루어지는 경우 찾기 합수가 비효율적으로 동작
  - 최악의 경우에 찾기 함수가 모든 노드를 다 확인하게 되어 시간 복잡도가 O(V)이다
- 찾기 함수 최적화 방법 => 경로 압축

```python
#특정 원소가 속한 집합을 찾기
def find_parent(parent, x):
    #루트 노드가 아니라면, 루트 노드를 찾을 때까지 재귀적으로 호출
    if parent[x] != x:
        parent[x] = find_parent(parent, parent[x])
	return parent[x]
```

## 서로소 집합을 활용한 사이클 판별

- 서로소 집합은 무방향 그래프 내에서의 사이클을 판별할 때 사용할 수 있음
  - 방향그래프에서의 사이클 여부는 DFS를 이용하여 판별
- 각 간선을 하나씩 확인하며 두 노드의 루트 노드를 확인
  - 루트 노드가 서로 다르다면 두 노드에 대하여 합집합(union) 연산 수행
  - 루트 노드가 서로 같다면 사이클이 발생한 것
- 그래프에 포함되어 있는 모든 간선에 대하여 1번 과정을 반복

- steps
  1. 초기단계: 모든 노드에 대하여 자기 자신을 부모로 설정하는 형태로 부모 테이블을 초기화
  2. step1: 간선 (1,2) 를 확인합니다. 노드1과 노드2의 루트 노드는 각각 1과 2입니다. 따라서 더 큰 번호에 해당하는 노드 2의 부모 노드를 1로 변경
  3. step2:  간선(1, 3)을 확인합니다. 노드 1과 노드 3의 루트 노드는 각각 1과 3입니다. 따라서 더 큰 번호에 해당하는 노드 3의 부모 노드를 1로 변경합니다.
  4. step3 : 간선 (2, 3)을 확인합니다. 이미 노드2와 노드3의 루트 노드는 모두 1입니다. 즉, 사이클이 발생한다는 것을 알 수 있다.

![image-20220128190205468](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220128190205468.png)

```python
#특정 원소가 속한 집합을 찾기
def find_parent(parent, x):
    #루트 노드가 아니라면, 루트 노드를 찾을 때까지 재귀적으로 호출
    if parent[x] != x:
        parent[x] = find_parent(parent, parent[x])
	return parent[x]

#두 원소가 속한 집합을 합치기
def union_parent(parent, a, b):
    a = find_parent(parent, a)
    b = find_parent(parent, b)
    if a < b:
        parent[b] = a
	else:
        parent[a] = b
        
#노드의 개수와 간선(union 연산)의 개수 입력 받기
v, e = map(int, input().split())
parent = [0] * (v +1) #부모 테이블 초기화하기

#부모 테이블상에서, 부모를 자기 자신으로 초기화
for i in range(1, v+1):
    parent[i] = i
    
cycle = False #사이클 발생 여부

for i in range(e):
    a, b(int, input().split())
    #사이클이 발생한 경우 종료
    if find_parent(parent, a) == find_parent(parent, b):
        cycle = True
        break
    #사이클이 발생하지 않았다면 합집합(union) 연산 수행
    else:
        union_parent(parent, a, b)

if cycle:
    print('사이클이 발생했습니다')
else:
    print('사이클이 발생하지 않았습니다')
```

