## 정렬 알고리즘

- 정렬이란 데이터를 특정한 기준에 따라 순서대로 나열하는 것

1. 선택정렬
   - 처리되지 않은 데이터 중에서 가장 작은 데이터를 선택해 맨 앞에 있는 데이터와 바꾸는 것을 반복
     - step0~끝: 처리되지 않는 데이터 중 가장 작은 '0'을 선택해 가장 앞의 7과 바꿉니다.  이 것을 반복 수행.

![image-20220125215016693](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220125215016693.png)

### 선택 정렬 소스코드

```python
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(len(array)):
    min_index = i
    for j in range(i+1, len(array)):
        if array[min_index] > array[j]:
            min_index = j
    array[i], array[min_index] = array[min_index], array[i] # 스왑해줌
print(array)

결괏값: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

- 시간 복잡도 : O(N^2)

2. 삽입 정렬 : 처리되지 않은 데이터를 하나씩 골라 적절한 위치에 삽입. 선택 정렬에 비해 구현 난이도가 높지만 더 효율적임

```python
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(1, len(array)):
    for j in range(i, 0, -1): # 인덱스 i부터 1까지 1씩 감소하며 반복하는 문법
        if array[j] < array[j-1]: #한 칸씩 왼쪽으로 이동
            array[j], array[j-1] = array[j-1], array[j]
        else:
            break
print(array)
```

- 시간 복잡도:  O(N^2)
