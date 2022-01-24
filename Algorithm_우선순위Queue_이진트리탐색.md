## Algorithm - 우선순위Queue(이진트리탐색)

- 기본적으로 트리의 크기가 N일때, 전체 간선의 개수는 n-1개

1. 이진 탐색 트리 steps
   - step1: 루트 노드부터 방문하여 탐색 진행
     1) 현재 노드와 찾는 원소를 비교
     2) 찾는 원소가 더 크면 오른쪽, 작으면 왼쪽 이동
   - step2: 현재 노드와 값을 비교
     1. 현재 노드와 찾는 원소를 비교
     2.  찾는 원소가 더 작으면 왼쪽, 크면 오른쪽
   - step3: 현재 노드와 값을 비교
     1. 현재 노드와 찾는 원소를 비교
     2. 원소를 찾으면 탐색 종료

![image-20220120185427721](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220120185427721.png)

```python
class Node:
	def __init__(self, data, left_node, right_node):
		self.data = data
		self.left_node = left_node
		self.right_node = right_node

#전위 순회(처음부터순회 하면서 왼쪽 먼저)
def pre_oreder(node):
    print(node.data, end=' ')
    if node.left_node != None:
        pre_order(tree[node.left_node])
    if node.right_node != None:
        pre_order(tree[node.right_node])
        
#중위 순회(왼쪽 자식을 방문한 뒤에 루트를 방문)
def in_order(node):
    if node.left_node != None:
        in_order(tree[node.left_node])
    print(node.data, end=' ')    
    if node.right_node != None:
        in_order(tree[node.right_node])

#후위순회(왼쪽 자식으로 갔따가 오른쪽을 먼저 방문 후 루트를 방문)
def post_order(node):
    if node.left_node != None:
        in_order(tree[node.left_node])
    if node.right_node != None:
        in_order(tree[node.right_node])
    print(node.data, end=' ')    
    
n = int(input())
tree = {}

for i in range(n):
    data, left_node, right_node = input().split()
    if left_node =="None":
        left_node == None
    if right_node =="None":
        right_node == None
    tree[data] = Node(data, left_node, right_node)
    
pre_order(tree['A'])
print()
in_order(tree['A'])
print()
post_order(tree['A'])
```

