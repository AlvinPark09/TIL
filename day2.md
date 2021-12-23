#﻿﻿git/git hub 무작정 따라하기 (2)

개인적으로 배운 것을 복습하는 목적으로 작성하였습니다.

git과 git hub는 다르다.

git: local에 프로젝트 파일을 올리고 그 파일을 관리할 수 있는 저장소(commit 내역 등의 모든 작업 이력이 담겨 있음)

git hub: 각종 소스코드를 오픈 소스로 누구에게나 공개한다는 가정하에 무료로 제공하는 원격 저장소(remote repository)

![img](https://blogfiles.pstatic.net/MjAyMTEyMjFfMTQx/MDAxNjQwMDg1NDUyMDMw.7lIJocQI5BexAGGknP4EkCJxCW8p_xW10MzocdsftBsg.UnMrW0wP931_nOF1jtrremGhS_JsKIkSYPrYSuRKkekg.PNG.cubix122/Untitled_(1).png?type=w1)

대표사진 삭제

대충 git이 작동하는 방법이랄까? 출처) 제가 교육 받은 강사님

1. git 초기 설정

처음 사용할 때 '한 번만' 설정하면 됩니다!

누가 파일을 커밋했는지 확인할 수 있게 이름과 이메일을 설정 (나중에 git hub 가입 시 사용할 email 사용)



```javascript
$ git config --global user.name "내이름"
$ git config --global user.email "이메일@naver.com"

$ git config --global --list 
#올바르게 설정 됐는지 확인!
```

2. git 기본 명령어
   1) git init

현재 작업 중인 디렉토리를 git으로 관리한다는 명령어로 .git (숨김폴더)가 생성, 터미널엔 (master)라고 표시됨



```javascript
$ git init
Initialized empty Git repository in C:/Users/psw/git-practice/.git/.

Psw@Psw-PC MINGW64 ~/GIT-PRACTICE (master)
```

​		2.git status

Working directory와 staging area에 있는 파일의 상태를 알려누는 명령어로 작업을 시행하기 전에 수시고 status를 확인하는 습관을 들이자



```javascript
$ git status
On branch master

no commits yet

nothing to commit(create/copy files and use "git add" to track)
#commit할 파일이 없으니 'git add'를 사용해 파일을 추가해야 한다
```

※상태

Untracked : Git이 관리하지 않는 파일 (한번도 Staging Area에 올라간 적 없는 파일)

Tracked : Git이 관리하는 파일

Unmodified : 최신 상태

Modified : 수정되었지만 아직 Staging Area에는 반영하지 않은 상태

Staged : Staging Area에 올라간 상태

​		3. git add

Working directory에 있는 파일을 Staging area로 올리는 명령어로 git이 해당 파일을 관리할 수 있도록 만듬

Untracked, Modified -> Staged 로 상태가 바뀜

```javascript
#특정 파일
$ git add a.txt

# 특정 폴더
$ git add folder/

#현재 디렉토레에 속한 파일/폴더 전부
$git add .
```

ex)

```javascript
$ touch a.txt b.txt     # a.txt b.txt 생성

$ git status    #상태확인!
On branch master

No commits yet

Untracked files:  # 트래킹 되고 있지 않는 파일 목록
  (use "git add <file>..." to include in what will be committed)
        a.txt
        b.txt

nothing added to commit but untracked files present (use "git add" to track)
```

```javascript
$ git add a.txt    # a.txt파일을 Staging Area로!
```

```javascript
$ git status

On branch master

No commits yet

Changes to be committed:        # 커밋 예정인 변경사항(Staging Area)
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt

Untracked files:                # 트래킹 되고 있지 않은 파일
  (use "git add <file>..." to include in what will be committed)
        b.txt
```

​		4.git commit

Staging Area에 올라온 파일 변경 사항을 하나의 버전으로 저장하는 명령어로 커밋 메세지는 의미있게 작성하는 것을 권장함.

(root-commit)은 해당 커밋이 최초의 commit을때만 표시됨. 이후 commit부터 사라짐

```javascript
$ git commit -m "first commit"     #커밋하는 명령어 // git commit -m "메세지" 
[master (root-commit) c02659f] first commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```

​		5. git log

commit의 내역(ID, 작성자, 시간, 메세지 등)을 조회 하는 명령어

```javascript
$ git log    

commit 1870222981b4731d14ef91d401c68c0bbb2f6e7d (HEAD -> master)
Author: Alvin <abc@naver.com>
Date:   Thu Dec 9 15:26:46 2021 +0900

    first commit
```

※옵션 (하이픈(-) 갯수 확인)

--oneline : 한 줄로 축약해서 보여줍니다.

--graph : 브랜치와 머지 내역을 그래프로 보여줍니다.

--all : 현재 브랜치를 포함한 모든 브랜치의 내역을 보여줍니다.

--reverse : 커밋 내역의 순서를 반대로 보여줍니다. (최신이 가장 아래)

-p : 파일의 변경 내용도 같이 보여줍니다.

-2 : 원하는 갯수 만큼의 내역을 보여줍니다. (2 말고 임의의 숫자 사용 가능)





지금까지는 git (local 관리)을 배웠습니다!

다음시간에는 git hub(remote repository)에 대해서 올리겠습니다~

﻿https://blog.naver.com/cubix122/222601221779
