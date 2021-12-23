

개인적으로 배운 것을 복습하는 목적으로 작성하였습니다.



git hub는 이 전 포스팅에도 말했듯이 remote repository를 무료로 이용할 수 있지만 오픈소스로 코드를 모두 오픈해야 합니다.



1. git hub 가입하기!

https://github.com/

![GitHub: Where the world builds software](https://dthumb-phinf.pstatic.net/?src=%22https://github.githubassets.com/images/modules/site/social-cards/github-social.png%22&type=ff500_300)

**GitHub: Where the world builds software**

GitHub is where over 73 million developers shape the future of software, together. Contribute to the open source community, manage your Git repositories, review code like a pro, track bugs and feat...

github.com

여기에 가입을 하는데 반드시 본인이 git에서 설정했던 email로 만드셔야합니다.



가장 먼저 해야할 것

2. setting

![img](https://blogfiles.pstatic.net/MjAyMTEyMjJfMjk2/MDAxNjQwMTcwMjYxMDY3.GM9i87EqZ0HKT2iMbs68a9ZotwjAF-DXszd8EqfB7zgg.MZE4bSsk-Ead2yUniumJyMDvOTX21KTpYj88GR10QOwg.PNG.cubix122/Untitled.png?type=w1)

대표사진 삭제

사진 설명을 입력하세요.

setting -> repositories -> main을 master로 바꿔준다.

나중에 push, 즉 git hub에 전송할 때 문제가 될 수 있다.



3. remote repository(원격 저장소) 만들기



![img](https://blogfiles.pstatic.net/MjAyMTEyMjJfMTc4/MDAxNjQwMTcyODI3Mzc4.WfrtUvkuiIUmwOdbvsartCr9A3g68wUga4jwFZ1tEDgg.iQxWYQRKFHMG6Gka4Z367oV9Aty5-EJXZHPAVrQ5-s4g.PNG.cubix122/11.png?type=w1)

대표사진 삭제

사진 설명을 입력하세요.

위 노란 박스 안에 보면 create repository 라고 있거나 오른쪽 위 (+) 버튼을 누르면 new repository라고 있으니 만들면 된다.

![img](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI5MzYiIGhlaWdodD0iODA0IiB2aWV3Qm94PSIwIDAgOTM2IDgwNCI+PHJlY3Qgd2lkdGg9IjEwMCUiIGhlaWdodD0iMTAwJSIgZmlsbD0iI0ZDRkNGQyIvPjwvc3ZnPg==)

사진 삭제

사진 설명을 입력하세요.

노란 박스에 원하는 저장소이름과 public, 아래 모든 항목은 check하지 말고 만들면 됩니다.

![img](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMzA5IiBoZWlnaHQ9IjUxMCIgdmlld0JveD0iMCAwIDEzMDkgNTEwIj48cmVjdCB3aWR0aD0iMTAwJSIgaGVpZ2h0PSIxMDAlIiBmaWxsPSIjRkNGQ0ZDIi8+PC9zdmc+)

사진 삭제

사진 설명을 입력하세요.

본인이 만든 repository를 클릭하고 Code를 클릭하면 아래 본인 repository의 주소가 나오는데 copy를 합니다.



4. local repository를 git hub에 연결하기 ($ git remote)



```javascript
$ git remote add <이름> <주소> 형식으로 대게 이름은 origin으로 많이 한다고 합니다.'
```

본인이 git hub에 올리고자 하는 폴더에 가서 vscode를 열고 아래와 같이 입력합니다. (주소는 위에서 복사했던 주소를 가져옵니다)



```javascript
$ git remote add origin https://github.com/AlvinPark09/TIL.git
```

그리고 정상적으로 등록이 됐는지 git remote -v로 확인합니다.



```javascript
$ git remote -v
origin  https://github.com/AlvinPark09/TIL.git (fetch)
origin  https://github.com/AlvinPark09/TIL.git (push)
```

혹시 저장소 연결을 삭제를 원하면?



```javascript
$ git remote rm <이름>
$ git remote remove <이름>

$ git remote rm origin 
#위의 연결을 끊길 원하면 이렇게
```

5. remote repository에 업로드 하기

   1) 업로드 하고자 하는 파일을 add & commit 한다.

   2) commit한 파일을 push하여 remote repository에 업로드한다

```javascript
$ git add TIL.md
$ git commit -m "first commit"    
$ git push -u origin master       #push할때 -u를 해주면 앞으로는 git push로만 업로드 가능

Enumerating objects: 5, done.      
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 306 bytes | 153.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 
remote: Resolving deltas: 100% (1/1), completed with 
1 local object.
To https://github.com/AlvinPark09/TIL.git
   9ac27c1..5c57e6c  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

위와 같은 100% 어쩌구 메세지가 나오면 제대로 업로드 됐다는 것입니다!

만약 처음 push 할때 뭔가 인증? 하라고 나오는데 그냥 확인하시고 진행 하시면 됩니다.

6. remote repository 가져오기 ( clone & pull)

clone(복제) - 현재 로컬 저장소가 없는 컴퓨터에서 git hub에 있는 저장소를 복제해서 내 컴퓨터에 똑같은 복제본을 만드는 의미로 없던 것을 새로 만든다고 생각하시면 쉽습니다. 한 번만 실행하면 됩니다.

pull(가져오기) - pull은 push의 반대로 실행하는 명령어로 git push처럼 local과 remote를 동기화 시키고 싶다면 사용하게 됩니다. 즉, 원래 있었던 파일에 덮어 쓴다고 생각하면 쉽죠!

```javascript
#clone시
$ git clone https://github.com/AlvinPark09/TIL.git  #<< 아까 복사했던 주소를 사용

#pull시
$ git pull origin master
```

7. README.md 파일을 push하여 연습해보기

README.md 는 본인의 저장소의 소개와 설명을 써놓는 대문 역할을 합니다.

(※주의 반드시 README.md로 push 해야 합니다.

![img](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMzg3IiBoZWlnaHQ9IjY0OSIgdmlld0JveD0iMCAwIDEzODcgNjQ5Ij48cmVjdCB3aWR0aD0iMTAwJSIgaGVpZ2h0PSIxMDAlIiBmaWxsPSIjRkNGQ0ZDIi8+PC9zdmc+)

push를 하면 위와 같이 나타납니다. (저는 일단 초보라 짧게 ㅎㅎ)

8. .gitignore

.gitignore는 특정 파일 or 폴더를 git이 관리하지 못하도록 지정 하는 것으로 민감한 개인정보(전화번호, 계좌번호 비밀번호, API KEY 등등), 그 외에 없어도 되는 파일 종류 등이 있습니다.

※주의: .gitignore 파일은 .git 폴더와 동일한 위치에 생성. 제외하고자 하는 파일을 반드시 add 하기 전에 .gitignore에 장성해야 합니다. 안그러면 git은 관리 대상으로 인식하여 push하면 대참사가 일어날지도..

근데 뭘 제외시켜야 하지?

https://www.toptal.com/developers/gitignore

![gitignore.io](https://dthumb-phinf.pstatic.net/?src=%22https://www.toptal.com/developers/gitignore/img/preview@2x.png%22&type=ff500_300)

위 사이트에서 본인이 사용하는 OS, text editor, 사용하는 언어를 선택한 후 Create하시면 알아서 기본적인 것들을 제외시켜 줍니다. 단, 반드시 본인이 원하는 파일이나 폴더를 관리에서 제외하고자 하면 추가해서 push 하세요!

﻿

**제 개인적인 복습용 블로그에 올린 내용입니다.**

https://blog.naver.com/cubix122?Redirect=Update&logNo=222602200646