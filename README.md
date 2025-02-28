# GIT 저장 과정 (Local Repository to Remote Repository)

##  (git init) -> Local Repository생성 - Working Directory -> (git add) -> Staging Area -> (commit 명령어) -> WD의 작업내용 LR에 최종 반영 -> (git remote add origin 주소) -> RR 주소와 연결 -> (git push) -> LR내용 RR 최종반영

  

<gr>

  

# 각 명령어 소개

## 각 명령어 사이에 git status 명령어를 사용하여 현재 상태를 확인한다.

<gr>

  

## 1. git init  

>개인의 pc에 Local Repository를 생성하는 명령어이다. 이 폴더에 작업한 .Git파일이 저장된다.

1. git파일 생성 및 RR에 업로드에 사용할 파일을 생성 후 개발 툴에서 open file 한다.

2. New terminal 생성 후 터미널에 "git init" 명령어를 입력한다.

> 파일이 아직 untracked 상태이다.

  

<gr>

  

## 2. git add (사용 예시) - git add example.txt <- example.txt 파일 SA에 반영  

>Working Directory 에서 작업된 내용을 Staging Area (commit 대기구간) 로 반영시키는 명령어이다.    

>만약 add된 작업 내용의 추가나 수정이 이루어졌다면 다시 add 명령어로 SA구간에 반영시켜야한다.  

  

 >add 해야할 파일이 많다면 git add F1.txt F2.txt <- (F1.txt , F2.txt 파일 반영) 이처럼 "파일.확장자" 사이에 띄어쓰기로 구분하여 2가지 이상의 파일을 한번에 add 가능하다.

  

 >add . 을 입력하면 작업된 모든 파일을 add할 수 있다.

  

 > add를 하기전에 작업한 파일이 save 되어있는지 확인한다.

  

 <gr>

  

## 3. git commit -m "" <- "" 안에는 커밋메시지를 입력한다.

  

>SA 구간에 커밋대기중인 파일들을 커밋메세지와 함께 커밋하여 LR에 최종 반영시키는 명령어이다.  

  

>여기서 SA구간은 비어진 상태가 된다.  

  

>따라서 이미 커밋된 파일을 add 후 다른 커밋메세지와 함께 커밋하면 다른 버전으로 저장가능하다.

  

>커밋메시지 입력 시 다른 사람이 커밋된 파일의 내용이나 버전 등을 알아보기 쉽게 작성한다.

  

---------

  

# Working Directory - Staging Area - Local Repository 과정 이후엔 네트워크의 연결을 요구한다.

  

 <gr>

  

## 4. git branch -M main <-- 깃허브에서 RR생성 후 브랜치를 따로 생성하지 않았을 경우 기본으로 생성되는 main브랜치에 커밋을 저장하는 명령어이다.  

  

>브랜치는 커밋이 저장된다. 따라서 Local/Remote Repository에는 최종적으로 브랜치와 커밋만 존재하게 된다.

  

>만약 깃허브에서 따로 생성한 브랜치를 이용하고자 한다면 예) git switch Newbranch으로 가능하다.

  

>깃허브에서 브랜치를 생성하지 않았다면 예) git switch -c newbranch 로 브랜치 추가 및 커밋을 저장할 브랜치를 전환할 수 있다.

  

<gr>

  

## 5. git remote add  

### (사용 예시) - git remote add 1. [origin] 2. [https://github.com/(깃허브 사용자이름)/ (Remote Repository 이름)]

  

> 1번 []안 origin은 기본으로 설정되어 있는 remote의 이름이다. 다른 이름을 입력하면 다른 이름으로 생성가능하다.  

  

> 이 명령어는 로컬의 작업 내용을 RR과 연결해주는 역할을 한다.

  

<gr>

  

## 6. git push

> 로컬 브랜치를 RR에 업로드하는 명령어다.  

> 예) git push -u origin main <--origin 이라는 remote의 main 브랜치로 업로드한다는 뜻이다. git remote add 와 git branch 명령어에서 별도로 설정하지 않았다면 예시의 명령어를 그대로 사용해도 무방하다.

  

<gr>

  

## 7. git merge  

> 각각의 브랜치의 작업 내용을 합치는 명령어이다.  

  

>이미 운영되고 있는 main 브랜치에 수정할 사항이 발생할 경우, 독립된 작업브랜치를 별도로    

만들어 작업 후 작업브랜치의 결과물을 메인 브랜치와 병합시켜 main 운영에 지장없이 코드를 수정할 수 있다.  

  

>독립된 브랜치는 여러사람과 협업을 할 경우 커밋의 충돌을 방지할 수 있다.

  

<gr>

  

### 7-1 merge 작업 순서

1. main 브랜치와 독립된 [working branch] 생성  

  

2. git switch 명령어를 통해 작업 브랜치로 이동하여 작업

3. git add , git commit , git push 명령어를 통해 RR에 반영한다.

4. git switch 명령어를 통해 main 브랜치로 돌아온다.

5. git merge [working branch] 을 통해 작업된 브랜치의 내용을 main에 반영한다.

6. 만약 merge conflict(충돌)이(가) 발생할 경우 개발자간의 완만한 협의 후에 해결한다.  

(되도록 다른 브랜치를 맡아서 작업하는게 좋다.)

7. 수정 작업시간 동안 main의 운영에 지장없이 작업내용이 반영된다.

  

<gr>

  

## 8. git clone

>RR의 폴더와 파일을 내 Local로 가져올 수 있다.

  

>cmd(명령프롬프트)에서 git clone remote주소 를 입력하면된다.

  

>LR에 없는 작업물을 다운받아 작업하기 때문에 다른 개발자와 동일한 파일의 작업이 가능해진다.

  

<gr>

  

## 9. git fetch

>작업 중인 파일의 변경사항을 내 RR에 반영하도록 하는 명령어이다.

  

>다른 개발자와 동일한 파일 작업을 할 경우 RR에 반영된 내가 모르는 커밋이 있는지 그래프를 통해 확인이 가능하다.

  

>RR에만 반영이되기 때문에 내 로컬에는 반영되지 않는다.

  

<gr>

  

## 10. git pull

>RR에 push된 내용을 내 로컬로 가져와 병합까지하는 명령어이다.

  

>다른 개발자가 작업한 커밋이 있는지 git fetch 명령어로 확인했다면 git pull origin [브랜치이름]을 통해

내 로컬에 반영시킬수 있다.

  

>바로 사용가능한 명령어지만 git fetch를 통해 확인하는것을 권장한다.

  

<gr>

  

# PR (Pull Request)####

> PR은 작업브랜치의 push된 커밋을 최종적으로 merge할 것인지 협의를 거쳐 최종 반영하는 과정이다. 다른 개발자와 협업시 필수이다.

  

> 협업시에는 git merge 명령어를 사용하지 않는다.

  

>작업할 작업물이 있는 저장소 fork를 한다.

  

>git clone을 통해 fork한 작업물의 폴더와 파일을 다운로드하고, git remote 명령어로 push할 remote의 주소와 연결한다.

  

>작업용 브랜치를 만들어 작업 후 commit을 push한다.

  

> 관련된 개발자를 깃허브 Contributors에 추가 후에 작업된 Commit에 대한 Pull Request 버튼을 눌러 요청하면 관련된 개발자들의 Review 와 comments확인 후 최종 수정된 commit의 결과 만족시  pull request merge 버튼을 통해 Main 브랜치에 최종반영하게 된다.

  

>병합이 끝나면 작업용 브랜치는 삭제한다.