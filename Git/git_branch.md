## Git branch 🏋️‍♂️

브랜칭(branching)은 기존 개발중인 메인 개발 코드를 그대로 복사하여 새로운 기능 개발을 메인 개발 코드를 건드리지 않고 할 수 있는 버전 관리 기법
처음에 Git 리포지토리를 생성하면 나오는 main 브랜치에서만 작업을 하다가 새로운 기능 개발을 위해 feature 브랜치를 새로 생성하는 경우, 기존 main 브랜치에서의 작업은 유지하고 새로운 feature 브랜치에서 자유롭게 코드를 추가 및 삭제 가능


### 브랜치 생성 / 및 변경 (git switch)

브랜치를 생성할 때는 생성(create)의 의미로 -c 를 붙여줘야 하고, 기존에 있는 브랜치로 옮길 때는 붙이지 않아도 된다.

> yb라는 브랜치를 새로 생성하는 경우 -c를 붙인다. git switch -c feature

### checkout이라는 명령어도 사용할 수 있다. git checkout -b feature

# 기존에 있던 main 브랜치로 HEAD를 변경하려면, -c를 붙이지 않습니다.
git switch main
git checkout main


> git switch yb 와 git checkout -b yb 의 차이가 무엇이냐면 
> git checkout -b yb : '새로운' yb 브랜치를 생성하고 switch한다.
> git switch yb : '기존' yb브랜치로 switch 한다 .


### 브랜치 합치기 ( git merge) 

- 기능 개발이 끝나면 브랜치를 main 브랜치와 합칠 수 있다
ex) 
>  기능 개발이 진행
git commit -m "기능1의 세부 기능1"
git commit -m "기능1의 세부 기능2"
git commit -m "기능1 개발 완료"

- 머지를 위해 main 브랜치로 전환
git switch main

- main 브랜치로 yb 브랜치를 병함
git merge yb


> 실제 프로젝트 개발 시에는 브랜치를 로컬에서 합치기 보다는 Github의 pull request 기능을 이용하여 변경 내역을 충분히 확인하고 난 다음에 머지하는 경우가 더 많기 때문에, 로컬에서 머지하지 않고 feature 브랜치를 push하여 pull request를 요청하는 것을 권장

ex.
- 기능 개발이 진행
git commit -m "기능1의 세부 기능1"
git commit -m "기능1의 세부 기능2"
git commit -m "기능1 개발 완료"

- Github 리포지토리로 푸시.
git push origin yb

- Github에서 Pull Request 진행.


## ## Git Team branch 🏋️‍


1. git pull 
팀원이 업데이트한 코드를 받아온다

2. git branch 
현재의 branch 확인

3. 내가 작성할 코드를 위한 branch 만든다
git checkout -b [branch 이름]

4. git branch 
한번 더 내 branch 확인

5. 코드 작성 및 수정

6. git add .

7. git commit -m  "커밋할 제목"

8. git push origin [branch 이름]
현재 내가 쳐논 가지의 branch에 푸쉬한다.

9. 깃허브 사이트 이동

10. PR진행 (Pull & Request)

11. Merge 진행 완료 후 레포지토리에서 새로 만들었던 branch 지우기

12. 인텔리제이로 돌아오기

13. git branch 
현재 branch 위치 확인

14. 만들었던 가지에서 git pull origin dev-be 
합쳐진 dev-be의 코드를 받아옴 -> 안전하게 작업위해

15. git switch dev-be
dev-be branch로 이동

16. git pull 
dev-be도 업데이트된 내용 pull

17. git push -d [새로만들었던 가지]
새로 만든 가지 지우기 ,


