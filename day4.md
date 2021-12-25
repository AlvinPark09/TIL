# 모두의 데이터분석 with 파이썬 (병아리반 복습)
### 기초
names = ['쵸파','루피','상디','조로']
names.append('해적왕')
for name in names:
    if len(name) > 2:
        print(name, '왔나요~?')
        

name = input("이름을 입력해주세요 : ")
print(name +'님! 안녕하세요!')

age = int(input('나이를 입력해주세요! : '))
print(age-4)

age = input('나이를 입력해주세요! : ')
print(int(age)-4)

name = input('이름을 입력해주세요 : ')
age = int(input('나이를 입력해주세요 : '))
print(f'안녕하세요! {name}님! 저는 처음에 {age-4}살인 줄 알았어요!!')

### 연산자

print(3 * 10)   #30, 곱셈
print(3**10)    #59049, 10의 제곱
print(3%10)     #3, 나머지
print(3/2)      #1.5, 실수 몫
print(3//2)     #1 , 정수 몫

### 비교 연산 (boolean)
print(10 >= 3)    #True 
print(10<=3)      #False
print(10==3)      #False   ==: 같다
print(10!=3)      #True    !=: 같지 않다
print(3%2 == 1)     #True    나머지가 1인가

### 논리 연산
print(1==1 and 2!=1)    #True 1==1과 2!=1 둘 다 조건 충족
print(10%2 != 0 and 1+1>0)  # False  1+1>0의 조건만 충족이다

print(10 < 5 or 10 ==5)   #False 둘 중 어느 조건도 충족x
print(10%2 !=0 or 1+1>0 ) #True 1+1>0 하나라도 조건 충족

import random  #랜덤 함수 import
dice = random.randint(1,6)    #정수 1이상 6이하 랜덤 추출
print(dice)]
    
#반복과 선택
#for문
name = '파이쏭'
for i in name:
    print(i)

names= ['쵸파','루피','상디','조로']
for i in names:
    print(i)

for i in [0,1,2,3]:
    print(i**2) #제곱값 보여줌

for i in range(100):
    print(i**2)
    
for i in range(1,101,2):
    print(i)
    
#if 조건문
if 10 != 0 and 5 % 2 == 1:
    print('안녕하세요!')
    
passwd = int(input('비밀번호 4자리를 입력하세요: '))
if passwd == 1234:
    print('비밀번호가 일치합니다.')
    
for i in range(10000):
    if i == 1234:
        print('비밀번호가 일치합니다.')
        
passwd = int(input('비밀번호 4자리를 입력하세요: '))
if passwd == 1234:
    print('비밀번호가 일치합니다.')
else:
    print('비밀번호가 일치하지 않습니다.')
    

print('[ 소름끼치도록 놀라운 심리테스트 ]')
menu = input('당신이 좋아하는 음식을 입력해주세요: ')
if menu == '짜장면':
    print('당신은 짜장면을 좋아하는 사람입니다.')
elif menu == '아이스크림':
    print('당신은 아이스크림을 좋아하는 사람입니다.')
elif menu =='사탕':
    print('당신은 사탕을 좋아하는 사랍입니다.')
else:
    print('당신은 짜장면과 아이스크림과 사탕을 좋아하지 않는 사람입니다.')
    
for i in [0,1,2,3]:
    print(i**2)    

names = ['쵸파','루피','상디','조로']
print(names[-1])  #조로 맨뒤, 꺼꾸로 -마이너스
for i in names:
    print(i)    
    
#index slices
print(names[0:2])
print(names[0:3:2])    #['쵸파', '상디'] 0,2,4 2칸씩 띄어서

#리스트 값 추가
names.append('나미')    
print(names)
print(len(names))   #5 문자열 길이

