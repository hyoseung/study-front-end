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
* 로컬에 새로운 브랜치 생성 : `git branch [branch 이름`\]
* 로컬 브랜치 삭제 : `git branch -d [branch 이름`\]
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
2. `git merge develop`  \(feature/test &lt;- develop, fast-forward 됨\)

## stash

* `git stash`
* `git stash list`
* `git stash pop 이름(stash@{0})`

## reset으로 commit 되돌리기

reset하고자 하는 commit으로 돌아간 후, 해당 커밋 이후의 이력을 전부 삭제한다.

reset기능은 혼자만 사용하는 branch 이거나, 다른 사람들이 해당 branch를 받은 적이 없다고 확인된 경우에 사용하는 것이 좋음

* `git reset [--옵션] [돌아갈 커]`
  * hard : 돌아간 커밋 이후의 변경 이력을 모두 삭제
  * mixed : 변경 이력은 전부 삭제되지만 변경된 내용에 대해서는 남아 있음
  * soft : 변경 이력은 전부 삭제하지만 변경된 내용에 대해서는 남아있
* 강제 푸시 : `git --force push origin [branch 명]`



