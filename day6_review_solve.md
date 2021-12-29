# 배웠으니 복습하기



1. (조건문(if)과 반복문(while, for))

연습문제1)  1~10까지 총 합을 구하시오

```python
sum = 0
for i in range(1,11):
    sum += i
print(sum)
```





연습문제2) 1~100까지 짝수 총합

```python
sum = 0
for i in range(1,101):
    if i % 2 ==0:
        sum += i
print(sum)
```



2. (함수(def), lambda, map)

연습문제)  리스트에서 하나의 숫자를 받고 10보다 크면 3을 곱하고, 작거나 같으면 2를 곱한다

```python
l2 = [5, 10, 15, 20]
result = []
for i in l2:
    if i > 10:
        result.append(i*3)
    else:
        result.append(i*2)
print(result)
```



3. (numpy 기초)

연습문제) a2에서 1, 3 행 선택 & 1,3열 선택

```python
a2 = np.array([[1,2,3,],[4,5,6],[7,8,9]]) 

#array([[1, 2, 3], 

#​      [4, 5, 6],         

#​      [7, 8, 9]])

a2[[0,2],[0,2]]
```



4. (pandas 기초 method)

연습문제)천단위 구분 문자 ','를 지우고 int로 바꾼 후 리스트의 합을 구하여라



```python
s3 = Series(['1,200','3,000','4,000'])
s3.map(lambda x: int(x.replace(',',''))).sum()
```



연습문제) 이메일 아이디를 추출하여 리스트에 담아라



```python
s4 = Series(['drwill@naver.com','zzuyu@drwill.kr'])
list(s4.map(lambda x: x.split('@')).str[0])
list(map(lambda x,y: x[0:y],s4, s4.str.find('@')))
```



5. (loc, iloc, 연산)

연습문제) 리스트 내의 a를 모두 대문자로 바꾸어라 replace를 사용

```python
l1 = ['abcd','abcde','aabb'] 
list(map(lambda x: x.replace('a','A'), l1))
```



6. (pandas replace)

연습문제) df1에 천단위 구분기호를 제거 후 모두 숫자로 변경하라(hint: apply map을 사용해도 괜찮다)

```python
df1 = DataFrame([['1,200', '1,300'],['1,400','1,500']])
df1.applymap(lambda x: int(x.replace(',','')))
```

