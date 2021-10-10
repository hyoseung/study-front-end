# 명령어

## 기본 동작

* 코드 가져오기 : `git clone [url]`
* stage올리기 : `git add .`
* commit 하기 : `git commit -m "commit 내용"`
* `git push [원격 저장소 이름] [로컬 브랜치 이름]`
* `git pull  [원격 저장소 이름] [로컬 브랜치 이름]`



## 환경

* config 확인 : `git config --list`
* 커밋이력 확인 : `git log --oneline`

## branch 관련

* 원격 브랜치 목록 : `git branch -r`
* 로컬 브랜치 목록 : `git branch -a`
* 현재 브랜치 확인 : `git branch -v`
* 로컬에 새로운 브랜치 생성 : `git branch [branch 이름`]
* 로컬 브랜치 삭제 : `git branch -d [branch 이름`]
* 현재 브랜치 상태 : `git status`
* 브랜치 이동 : `git checkout [branch 이름]`
* git 원격 브랜치 tracking 삭제 : `git branch --delete --remotes origin/main`
* git 원격 브랜치 삭제 : `git push origin --delete [원격 branch명]`
* 로컬 branch 새로 생성 후 이동 : `git checkout -b [로컬 branch ]`
* 로컬 branch 이름 변경 : `git branch -m [변경할 branch 명]`
* 로컬 branch를 원격에도 생성하고 싶을 경우 : `git push origin [로컬 branch 명]`

## commit이 앞서있는 경우

local develop branch가 feature/test branch보다 commit이 앞서있는 경우

1. `git checkout feature/test`
2. `git merge develop`  (feature/test <- develop, fast-forward 됨)

## stash

* `git stash`
* `git stash list`
* `git stash pop 이름(stash@{0})`

## reset으로 commit 되돌리기

reset하고자 하는 commit으로 돌아간 후, 해당 커밋 이후의 이력을 전부 삭제

reset기능은 혼자만 사용하는 branch 이거나, 다른 사람들이 해당 branch를 받은 적이 없다고 확인된 경우에 사용하는 것이 좋음

* `git reset [--옵션] [돌아갈 커밋]`
  * hard : 돌아간 커밋 이후의 변경 이력을 모두 삭제
  * mixed : 변경 이력은 전부 삭제되지만 변경된 내용에 대해서는 남아 있음
  * soft : 변경 이력은 전부 삭제하지만 변경된 내용에 대해서는 남아있음
* 강제 푸시 : `git --force push origin [branch 명]`

## rebase으로 merge 하기

* `rebase`는 말 그대로 re-base 베이스를 재배치한다는 뜻
* `merge`를 사용하면 히스토리 볼때 뿌리가 여러개로 나눠져있어서 보기 어려움
* `rebase`는 베이스를 정의함으로써 새롭게 커밋 라인을 정리하여 히스토리를 깔끔하게 볼수 있게 해줌

![](<../.gitbook/assets/image (40).png>)

위와 같은 상황에서 `feature/test`를 `develop`으로 `merge`를 하려고 할 때, `merge`대신 `rebase`를 한다.

1. `feature/test`로 `checkout`  (git checkout feature/test)
2. `git rebase develop`
   * gitkraken : rebase feature/test onto develop
   * sourcetree : develop(으)로 현재 바뀐 내용 재배치

![](<../.gitbook/assets/image (41).png>)

1. `develop`으 `checkout` (git checkout develop)
2. `git merge feature/test`
   * gitkraken : fast-forward develop into feature/test
   * sourcetree : Merge feature/test into develop

![](<../.gitbook/assets/image (43).png>)

## Commit message 수정하기

마지막 커밋 메시지 수정

* `git commit --amend -m "수정할 메시지"`
* `git push -f`
