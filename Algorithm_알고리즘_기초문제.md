## 알고리즘 기초문제

![image-20220126175647729](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220126175647729.png)

![image-20220126180616741](C:\Users\Psw\AppData\Roaming\Typora\typora-user-images\image-20220126180616741.png)

```python
n, k = map(int, input().split())
a = list(map(int, input().split()))
b = list(map(int, input().split()))

a.sort() # a 리스트 오름차순 정렬
b.sort(reverse=True) #b 리스트 내림차순 정렬

#첫 번째 인덱스부터 확인, 두 리스트의 원소를 최대 K번 비교
for i in range(k):
    #A의 원소가 B의 원소보다 작은 경우
    if a[i] < b[i]:
        #두 원소를 교체
        a[i], b[i] = b[i], a[i]
    else: #A의 원소가 B의 원소보다 크거나 같을 떄, 반복문을 탈출
        break

print(sum(a))


    
```

