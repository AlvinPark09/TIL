## 재귀1 - 별 쌓기

```python
def printStar(n):
	if n > 0 :
        printStar(n-1)
        print('★' * n)

print(5)

#★
#★★
#★★★
#★★★★
#★★★★★
```

 

## 재귀2 1-10까지 합 구하기

```python
def addNumber(num):
    if num <= 1:
        return 1
    return num + addNumber(num-1)
print(addNumber(10))

#55
```



## 재귀3 카운트다운

```python
def countDown(n):
    if n <= 0:
        print('!!!!발사!!!!')
        return
	else:
        print(n)
        countDown(n-1)

#5
#4
#3
#2
#1
#발사!!!!!!!  
```



