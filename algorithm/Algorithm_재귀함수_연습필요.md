## 재귀 함수

- 자기 자신을 다시 호출하는 함수
- 단순한 형태의 재귀 함수 예제
  - '재귀 함수를 호출합니다.' 라는 문자열을 무한히 출력
  - 어느 정도 출력하다가 최대 재귀 깊이 초과 메시지가 출력

```python
def recursive_function():
    print('재귀 함수를 호출합니다.')
    recursive_function()
recursive_function()
```

- 재귀 함수를 문제 풀이에서 사용할 떄는 재귀 함수의 종료 조건을 반드시 명시해야 합니다
- 종료 조건을 제대로 명시하지 않으면 함수가 무한히 호출될 수 있다
  - 종료 조건을 포함한 재귀 함수 예제

```python
def recursive_function(i):
    # 100번째 호출을 했을 때 종료되도록 종료 조건 명시
    if i == 100:
        return
    print(i, '번째 재귀함수에서', i+1, '번째 재귀함수를 호출합니다.')
    recursive_function(i + 1)
    print(i, '번째 재귀함수를 종료합니다.')
    recursive_function()

recursive_function(1)
```

- 팩토리얼 구현 예제

```python
#반복적으로 구현한 n!
def factorial_iterative(n):
    result = 1
    #1부터 n까지의 수를 차례대로 곱하기
    for i in range(1, n+1):
        result *= 1
    return result

#재귀적으로 구현한 n!
def factorial_recursive(n):
    if n <= 1:  #n이 1 이하인 경우 1을 반환
        return 1
    # n! = n(n -1)!을 그대로 코드로 작성
    return n * factorial_iterative(n - 1)

#각각의 방식으로 구현한 n! 출력(n = 5)
print('반복적으로 구현', factorial_iterative(5))
print('재귀적으로 구현', factorial_recursive(5))

```

## 최대공약수 계산 ( 유클리드 호제법) 예제

- 두 개의 자연수에 대한 최대공약수를 구하는 대표적인 알고리즘
- 유클리드 호제법
  - 두 자연수 A, B에 대하여(A>B) A를 B로 나눈 나머지를 R
  - 이때 A와 B의 최대 공약수는 B와 R의 최대공약수와 같다

```python
def gdc(a, b):
    if a % b ==0:
        return b
    else:
        return gcd(b, a % b)
```

### 재귀 함수 사용의 유의사항

- 재귀 함수를 잘 활용하면 복잡한 알고리즘을 간결하게 작성할 수 있다

  - 단, 오히려 다른사람이 이해하기 어려운 형태의 코드가 될 수 있으므로 신중하게 사용해야 함

- 모든 재귀 함수는 반복문을 이용하여 동일한 기능을 구현할 수 있습니다.

- 재귀 함수가 반복문보다 유리한 경우도 있고 불리한 경우도 있습니다

- 컴퓨터가 함수를 연속적으로 호출하면 컴퓨터 메모리 내부의 스택 프레임에 쌓입니다

  - 그래서 스택을 사용해야 할 때 구현상 스택 라이브러리 대신에 재귀함수를 이용하는 경우가 많다.

- 반복문 vs 재귀함수 다른점?

  - 반복문은 1~ n까지 차례대로 연산하지만 재귀함수는 n ~ 1까지 가장 마지막에 호출된 함수의 크기부터 차례대로 내림차순으로 연산됨.
  - ex) 반복문 -> 1+2+3+4+5 = 15
  - ex) 재귀함수 -> 5+4+3+2+1 = 15

  
