# 자료구조와 알고리즘

## 선형리스트 (기초)

```python
# -*- coding: utf-8 -*-
"""
Created on Mon Jan  3 21:29:47 2022

@author: Psw
"""
## 함수/클래스 선언분
class Node():
    def __init__ (self):
        self.data = None
        self.link = None

def printNode(start):
    current = start
    print(current.data, end= ' ')
    while current.link != None:
        current = current.link
        print(current.data, end=' ')
    print()

def insertNode(findData, insertData):
    global head, current, pre
    if head.data == findData:
        node = Node()
        node.data = insertData
        node.link = head
        head = node
        return
    #사나 앞에 솔라를 삽입
    current = head
    while current.link != None:
        pre = current
        current = current.link
        if current == findData:
            node = Node()
            node.data = insertData
            node.link = current
            pre.link = node
            return
    #마지막에 추가할 때(=삽입할 이름이 존재하지 않을때)
    node = Node()
    node.data = insertData
    current.link = node
    return

def deleteNode(deleteData):
    global current, pre, head
    #첫노드 삭제
    if head.data == deleteData:
        current = head
        head = head.link
        del(current)
        return
    # 첫 노드 외의 노드 삭제
    current = head
    while current.link != None:
        pre = current
        current = current.link         #current.link = current 오답
        if current.data == deleteData: #current == deleteData 오답
            pre.link = current.link
            del(current)
            return

def findNode(findData):
    global current, pre, head
    current = head
    if current.data == findData:
        return current
    while current.link != None:     #current != None 오답
        current = current.link
        if current.data == findData:
            return current
    return Node()

        
# 전역 변수
head, pre, current = None, None, None
dataArray = ['다현','정연','쯔위','사나','지효']

# 메인 코드부
node = Node() # 첫 노드
node.data = dataArray[0]
head = node

for data in dataArray[1:]:
    pre = node
    node = Node()
    node.data = data
    pre.link = node

printNode(head)

insertNode('다현','화사')
printNode(head)

insertNode('사나','솔라')
printNode(head)

insertNode('재남', '문별')
printNode(head)

deleteNode('화사')
printNode(head)

deleteNode('쯔위')
printNode(head)

deleteNode('재남')
printNode(head)

fNode = findNode('다현')
print(fNode.data)
fNode = findNode('사나')
print(fNode.data)
fNode = findNode('재남')
print(fNode.data)

```

