## 소수 여부를 빠르게 처리하는 알고리즘들

- 소수란 1보다 큰 자연수 중에서 1과 자기 자신을 제외한 자연수로는 나누어떨어지지 않는 자연수
  - 6은 1, 2, 3, 6으로 나누어 떨어지므로 소수가 아니다
  - 7은 1과 7을 제외하고 나누어 떨어지지 않으므로 소수
- 코딩 테스트에서는 어떠한 자연수가 소수인지 아닌지 판별해야 하는 문제가 자주 출제됨
- 기본 알고리즘: (시간 복잡도: O(X))

```python
#소수 판별 함수(2 이상의 자연수에 대하여)
def is_prime_number(x):
    #2부터 (x - 1)까지의 모든 수를 확인하며 (1과 자기 자신을 뺀 나머지)
    for i in range(2, x):
        #x가 해당 수로 나누어떨어진다면
        if x % i ==0:
            return False #소수가 아님
	return True
print(is_prime_number(4))
print(is_prime_number(7))
#결괏값:
#False
#True
```

### 약수의 성질

- 모든 약수가 가운데 약수를 기준으로 곱셈 연산에 대해 대칭을 이루는 것을 알 수 있다
  - 예를 들어 16의 약수는 1,2,4,8,16이다
  - 이때 2 x 8 = 16은 8 x 2 = 16 과 대칭
- 따라서 특정한 자연수의 모든 약수를 찾을 때 가운데 약수(제곱근)까지만 확인
  - 예를 들어 16이 2로 나누어떨어진다는 것은 8로도 나누어떨어진다는 것을 의미
- 개선된 알고리즘: ( 시간 복잡도: O(N**0.5) )

```python
import math
#소수 판별 함수(2 이상의 자연수에 대하여)
def is_prime_number(x):
    #2부터 x의 제곱근까지의 모든 수를 확인하며
    for i in range(2, int(x**0.5)+1): 
    #float으로 나와도 int로 바꿔줌
        #x가 해당 수로 나누어떨어진다면
        if x % i ==0:
            return False #소수가 아님
	return True
print(is_prime_number(4))
print(is_prime_number(7))
#결괏값:
#False
#True
```

## 에라토스테네스의 체 알고리즘

- 다수의 자연수에 대하여 소수여부를 판별할 때 사용하는 알고리즘
- N보다 작거나 같은 모든 소수를 찾을때 사용할 수 있음
- 알고리즘의 동작 과정
  1. 2부터 N까지의 모든 자연수를 나열한다
  2. 남은 수 중에서 아직 처리하지 않은 가장 작은 수 i를 찾는다.
  3. 남은 수 중에서 i의 배수를 모두 제거한다.(i는 제거하지 않는다)
  4. 더이상 반복할 수 없을 때까지 2번과 3번의 과정을 반복한다

- steps
  1. 초기단계: 2부터 26까지의 모든 자연수를 나열 (N = 26)
  2.  step1: 아직 처리하지 않은 가장 작은 수 2를 제외한 2의 배수를 모두 제거
  3. step2: 아직 처리하지 않은 가장 작은 수 3을 제외한 3의 배수를 모두 제거
  4. step3: 아직 처리하지 않은 가장 작은 수 5를 제외한 5의 배수를 모두 제거

```python
import math

n = 10000 #2부터 1,000까지의 모든 수에 대하여 소수 판별
#처음엔 모든 수가 소수(True)인 것으로 초기화(0과 1은 제외)
array = [True for i in range(n + 1)]

#에라토스테네스의 체 알고리즘 수행
# 2부터 n의 제곱근까지의 모든 수를 확인하며
for i in range(2, int(math.sqrt(n))+1):
    if array[i] == True:  #i가 소수인 경우(남은 수인 경우)
        # i를 제외한 i의 모든 배수를 지우기
        j = 2
        while i * j <= n:
            array [i * j] = False
            j += 1
# 모든 소수 출력
for i in range(2, n + 1):
    if array[i]:
        print(i, end =' ')
```

- 시간 복잡도: O(NloglogN)
- 사실상 선형 시간에 가까울 정도로 매우 빠름
