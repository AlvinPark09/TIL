## 이진 검색(실무 사용에도 좋음)

```python
import random
#함수
def binarySearch(ary, fData):
      pos = -1
      start = 0
      end = len(ary) -1
      while start <= end:
            mid = (start+end) // 2
            if fData == ary[mid]:
                  return mid
            elif fData < ary[mid]:
                  end = mid -1
            else:
                  start = mid + 1
      return pos
            

#전역
dataAry = [random.randint(1,99) for _ in range(10)]
findData = dataAry[random.randint(0,len(dataAry)-1)]
dataAry.sort()

#메인
print('배열-->', dataAry)
position = binarySearch(dataAry, findData)
if position == -1:
    print(findData, '없습니다.')
else:
    print(findData,'이(가)', position,' 위치에 있음')
```

