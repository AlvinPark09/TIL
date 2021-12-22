# CLI

1. CLI 와 GUI

   1. CLI(Command Line Interface): 터미널을 통해 사용자와 컴퓨터가 상호 작용하는 방식

      Ex) cmd, git-bash 등

   2. GUI(Graphic User Interface) : 그래픽을 통해 사용자와 컴퓨터가 상호작용하는 방식

      Ex) 윈도우 등

2. 터미널 명령어

   - touch: 파일을 생성. 띄어쓰기로 여러 파일 생성 가능

     ```
     $ touch a.txt
     $ touch test.txt
     ```

     

   - mkdir (make directory): 디렉토리 생성. 띄어쓰기로 여러 폴더 생성 가능

     ```
     $ mkdir 폴더명
     $ mkdir CLI
     $ mkdir TIL
     ```

   - rm (remove): 파일 or 폴더 삭제. GUI와 다르게 휴지통으로 가지 않고 바로 삭제(GUI의 shift+삭제와 같음)

     ```
     $ rm 파일명.확장명
     $ rm a.txt
     $ rm test.txt
     $ rm -r(recursive) 폴더명
     $ rm -r CLI
     $ rm -r TIL
     ```

   - ls (list segments): 현재 디렉토리의 폴더/파일 목록을 보여줌.

     - -a (all): 숨김 파일까지 모두 보여줌
     - -l (long): 용량, 수정 날짜 등 파일 정보를 자세히 보여줌

     ```
     #기본 사용
     $ ls
     
     # all
     $ ls -a
     
     # long
     $ ls -l
     
     혼합 사용
     $ ls -a -l
     $ ls -al
     ```

   - cd (change directory) : 디렉토리를 변경

     - `cd ~` : 홈 디렉토리 이동 (`cd`만 입력해도 동일)
     - `cd ..`: 상위 디렉토리 이동(위로가기)
     - `cd -` : 바로 전 디렉토리 이동(뒤로가기)

     ```
     #현재 위치에 있는 TIL폴더로 이동
     $ cd TIL 
     
     #원하는 디렉토리로 변경(절대 경로)
     $ cd /c/users/psw/desktop
     #상대 경로를 통한 디렉토리 변경
     $ cd ../parent/child
     ```

   - mv (move) : 폴더/파일을 다른 폴더 내로 이동하거나 이름을 변경

     ※주의: 다른 폴더로 이동할 때는 작성한 폴더가 반드시 있어야함. 없으면 이름이 바뀜.

     ```
     #text.txt를 TIL폴더 안에 넣기
     $ mv text.txt TIL
     
     #text.txt를 TIL.txt로 바꾸기
     $ mv text.txt TIL.txt
     ```

   ---

# 제목1 (# 제목1)

## 제목2 (## 제목2)

### 제목3 (### 제목3)

#### 제목4 (#### 제목4)

##### 제목5 (#####제목5)

###### 제목6 (###### 제목6 )

---

목록

순서가 없는 목록

- 목록1
- 목록2
- 과일
  - 수박
  - 참외
  - 바나나

-, *, + -> 순서가 없는 목록



순서가 있는 목록

1. 목록1
2. 목록2
   1. 하위1
   2. 하위2

---

강조(스타일링)

1. 기울임(이탤릭체): *글자* _글자_ (\_글자\_) or (\*글자\*)
2. 굵게(볼드체): **글자** __글자__
3. 취소선: ~~글자~~

---

코드

인라인코드(=한줄)

파이썬에서는 `print("Hello WOrld!")`라고 쓸 수 있습니다.



블록코드(=여러줄)

```python
for i in range(10):
	print(i)
```

---

수평선

-, *, _ 3번 연속 작성

---

표(table)

| 동물   | 다리개수 | 종     |
| ------ | -------- | ------ |
| 사자   | 4개      | 포유류 |
| 원숭이 | 2개      | 포유류 |
| 앵무새 | 2개      | 조류   |
|        |          |        |

문자열 이스케이프(백슬러쉬)

\'print()' ( \\'print()\\' )
