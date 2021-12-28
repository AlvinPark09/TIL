# 데이터 시각화 - matplotlib practice

```python
import csv
import matplotlib.pyplot as plt

f = open('./data/seoul_book.csv')
data = csv.reader(f)
next(data)

high = []
low = []
mean = []

#날짜[0]	지점[1]	평균기온[2]	최저기온[3] 최고기온[4]

for row in data:
   if row[3] != '' and row[4] != '':
       date = row[0].split('-')    #[yyyy, mm, dd]
       if date[0] >= '1983':
           if date[1] == '09' and date[2] == '04':
                high.append(row[-1])
                low.append(row[-2])
                mean.append(row[2])

plt.rc('font', family = 'Malgun Gothic')
plt.rcParams['axes.unicode_minus'] = False  #마이너스 기호 깨짐 방지
plt.title('내 생일날의 역대 기온 변화 그래프') #'hotpink'로 하려다 오류나서 지움
plt.plot(high, 'red', label = 'high')       #리스트 high를 빨강색으로 위치는 가장 윗쪽
plt.plot(low, 'skyblue', label = 'low')     #리스트 low를 하늘색으로 위치는 가장 아래쪽
plt.plot(mean, 'purple', label = 'middle')  #리스트 mean을 보라색으로 위치는 중간에
plt.legend()                                #범주 보여줘
plt.show()
```

어제 오늘 너무 게을렀다..
복습도 제대로 못하고 TIL도 못올렸다ㅠㅠ