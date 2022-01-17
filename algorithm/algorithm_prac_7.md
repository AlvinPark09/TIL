# 자료구조와 알고리즘

## 선형리스트 (기초)

```python
# -*- coding: utf-8 -*-
"""
Created on Mon Jan  3 23:21:00 2022

@author: Psw
"""

#함수
def add_data(friend):
    katok.append(None)
    kLen = len(katok)
    katok[kLen-1] = friend

def insert_data(position, friend):
    katok.append(None)
    kLen = len(katok)
    for i in range(kLen-1, position, -1):
        katok[i] = katok[i-1]
        katok[i-1] = None
        katok[position] = friend
    
def delete_data(position):
    katok[position] = None
    kLen = len(katok)
    for i in range(position+1, kLen):
        katok[i-1] = katok[i]
        katok[i] = None
    del(katok[kLen-1])   #kLen-1은 제일 마지막 노드
        
      
#전역
katok = []
#메인
add_data("다현")
add_data("정연")
add_data("쯔위")
add_data("사나")
add_data("지효")
print(katok)#['다현', '정연', '쯔위', '사나', '지효']
add_data('모모')          # 모모를 맨 뒤에 add
print(katok)#['다현', '정연', '쯔위', '사나', '지효', '모모']
insert_data(3, '미나')    # 3등으로 미나를 insert
print(katok)#['다현', '정연', '쯔위', '미나', '사나', '지효', '모모']
delete_data(4)            #사나 delete
print(katok)#['다현', '정연', '쯔위', '미나', '지효', '모모']
```

