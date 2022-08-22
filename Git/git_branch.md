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

