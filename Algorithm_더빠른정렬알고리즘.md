## 더 빠른 정렬 알고리즘: 퀵 정렬과 계수 정렬

1. 퀵 정렬
   - 기준 데이터를 설정, 그 기준보다 큰 데이터와 작은 데이터의 위치를 바꾸는 방법
   - 첫 번쨰 데이터를 기준 데이터(pivot)로 설정
   - step0~: 현재 피봇 값은 5, 왼쪽에서부터 5보다 큰 데이터를 선택하므로 7이 선택되고, 오른쪽에서부터 5보다 작은 데이터를 선택하므로 4가 선택. 이 두 데이터의 위치를 서로 변경

![image-20220125223318135](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220125223318135.png)

- 분할: 피봇인 5를 기준으로 왼쪽은 피봇보다 작은 수, 오른쪽은 큰 수로 데이터 묶음을 나누는 작업

![image-20220125223541044](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220125223541044.png)

- 시간복잡도: O(N logN) but 최악시 N^2

### 퀵 정렬 소스코드

```python
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array, start, end):
    if start >= end:
        return
   	pivot = start
    left = start+1
    right = end
    while(left <= right):
        #피봇보다 큰 데이터를 찾을 때까지 반복
        while(left <= end and array[left] < array[pivot]):
            left += 1
        #피봇보다 작은 데이터를 찾을 때까지 반복    
        while(right > start and array[right]>=array[pivot]):
            right -= 1
       	if left> right: # 엇갈렸다면 작은 데이터와 피봇 교체
            array[right], array[pivot] = array[pivot], array[right]
         else: #엇갈리지 않았다면 작은 데이터와 큰 데이터를 교체
            array[left], array[right] = array[right], array[left]
#분할 이후 왼ㅉ고 부분과 오른쪽 부분에서 각각 정렬 수행
	quick_sort(array, start, right-1)
	quick_sort(array, right+1, end)

quick_sort(array, 0, len(array)-1)
print(array)
```

 ### 퀵 정렬 소스코드(간결)

```python
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array):
    #리스트가 하나 이하의 원소만을 담고 있다면 종료
    if len(array) <= 1:
        return array
    pivot = array[0]
    tail = array[1:]
    
    left_side = [ x for x in tail if x <= pivot] # 분할된 왼쪽 부분
    right_side = [ x for x in tail if x > pivot] # 분할된 오른ㅉ고 부분
    
    # 분할 이후 왼쪽 부분과 오른쪽 부분에서 각각 정렬 수행하고, 전체 리스트 반환
    return quick_sort(left_side) + [pivot] + quick_sort(right_side)

print(quick_sort(array))
```



2. 계수 정렬
   - 데이터의 크기 범위가 제한되어 정수 형태로 표현할 수 있을때 사용 가능, 특정 조건이 부합할 때만 사용할 수 있지만 매우 빠르게 동작하는 알고리즘
   - 시간 복잡도 : O(N + K)
   - step: 데이터를 하나씩 확인하며 데이터의 값과 동일한 인덱스의 데이터를 1씩 증가시킴

```python
#모든 원소의 값이 0보다 크거나 같다고 가정
array = [7, 5, 9, 0, 3, 1, 6, 2, 9, 1, 4, 8, 0, 5, 2]
#모든 범위를 포ㅛ함하는 리스트 선언(모든 값은 0으로 초기화)
count = [0] * (max(array)+1)

for i in range(len(array)):
    count[array[i]] += 1 # 각 데이터에 해당하는 인덱스의 값 증가
for i in range(len(count)): #리스트에 기록된 정렬 정보 확인
    for j in range(count[i]): 
        print(i, end= ' ') #띄어쓰기를 구분으로 등장한 횟수만큼 인덱스 출력
```

