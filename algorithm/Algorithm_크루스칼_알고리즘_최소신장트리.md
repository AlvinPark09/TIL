## 크루스칼 알고리즘 : 최소 신장 트리를 찾는 알고리즘

- 그래프에서 모든 노드를 포함하면서 사이클이 존재하지 않는 부분 그래프를 의미
  - 모든 노드가 포함되어 서로 연결되면서 사이클이 존재하지 않는다는 조건은 트리의 조건이기도 함
- 최소한의 비용으로 구성되는 신장 트리를 찾아야 할 때
- 시간복잡도: 간선의 개수가 E개일 때, O(E logE)
- 동작 과정
  1. 간선 데이터를 비용에 따라 오름차순으로 정렬
  2. 간선을 하나씩 확인하며 현재의 간선이 사이클을 발생시키는지 확인
     1. 사이클이 발생하지 않는 경우 최소 신장 트리에 포함
     2. 사이클이 발생하는 경우 최소 신장 트리에 포함시키지 않음
  3. 모든 간선에 대하여 2번 과정 반복
- steps
  1. 초기단계: 그래프의 모든 간선 정보에 대하여 오름차순 정렬을 수행
  2. step1: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인 (3, 4)를 선택하여 처리(같은 집합에 속해있지 않아 합집합 연산 수행)
  3. step2: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인 (4,7)을 선택하여 처리
  4. step3:  아직 처리하지 않은 간선 중에서 가장 짧은 간선인(4, 6)을 선택하여 처리
  5. step4: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인(4, 7)을 선택하여 처리
  6. step5: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인(1, 2)을 선택하여 처리
  7. step6: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인(2, 6)을 선택하여 처리
  8. step7: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인(2, 3)을 선택하여 처리 (이미 같은 집합에 속하여 신장트리에 포함x)
  9. step8: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인(5, 6)을 선택하여 처리 (같은 집합에 속해있지 않아 합집합 연산 수행)
  10. step9: 아직 처리하지 않은 간선 중에서 가장 짧은 간선인(1, 5)을 선택하여 처리 (이미 같은 집합에 속하여 신장트리에 포함x)

![image-20220128202421889](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220128202421889.png)

결과

![image-20220128203010715](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220128203010715.png)

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

#모든 간선을 담을 리스트와, 최종 비용을 담을 변서
edges = []
result = 0

#부모 테이블 상에서 부모를 자기 자신으로 초기화
for i in range(1, v+1):
    parent[i] = i

#모든 간선에 대한 정보를 입력 받기
for _ in range(e):
    a, b, cost = map(int, input().split())
    #비용순으로 정렬하기 위해서 튜플의 첫 번쨰 원소를 비용으로 설정
    edges.append((cost, a, b))
    
#간선을 비용순으로 정렬
edges.sort()

#간선을 하나씩 확인하며
for edge in edges:
    cost, a, b = edge
    #사이클이 발생하지 않는 경우에만 집합에 포합
    if find_parent(parent, a) != find_parent(parent, b):
        union_parent(parent, a, b)
        result += cost
        
print(result)
```

