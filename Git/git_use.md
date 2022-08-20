
## Github에 처음으로 코드 업로드하기 🏋️‍♂️
1. 초기화
> git init

2. 추가할 파일 더하기
> git add .
.(점) 은 모든 파일이라는 뜻, 선택적으로 올리고 싶으면 add뒤에 파일 이름 붙여주면 됨 (예. git add index.html)

3. 상태 확인 (선택사항)
> git status

4.히스토리 만들기
> git commit -m "first commit"
-m 은 메세지의 준말로 뒤에 “” 안에 주고싶은 히스토리 이름을 주면 됨 (즉, first commit일 필요가 없다! )

5.Github repository랑 내 로컬 프로젝트랑 연결

> git remote add origin https://github.com/yongbin77/TIL.git  //예시 
이 명령어는 github에서 복사해서 붙여와야함 

6. 잘 연결됐는지 확인 (선택사항)
> git remote -v
내가 연결한 주소값이 잘 뜨면 성공!🎇

7. Github로 올리기
>git push origin master
master 자리에는 branch이름이 들어가면 됨 branch이름이 main라하면 git push origin main 이라고 써야함

Github에 계속 업데이트 하는법 🤹‍♂️
추가할 파일 더하기
git add .
히스토리 만들기
git commit -m "first commit"
Github로 올리기
git push origin master
내 컴퓨터에 소스코드를 업데이트를 하고 싶으면 이 세개의 스텝만 계속 반복하면 됨.

---------------------
## Github로 팀프로젝트 하는법 👨‍👩‍👧‍👦
1. Github에서 소스코드 다운로드
> git clone 주소 폴더이름
주소는 깃허브에서 들고와야함
폴더이름은 선택사항이다 (즉 없어도됨) 폴더이름을 줄경우에는 그 폴더가 새로 생성이 되면서 그 안에 코드들이 다운로드가 되고, 
폴더이름을 안줄경우엔 깃허브 프로젝트 이름으로 폴더가 자동으로 생기고 그안에 코드들이 다운로드된다.

2. Github에서 내 브렌치(branch)만들기
>git checkout -b 브렌치이름

3.내 브렌치에 소스코드 업데이트하기 (가지친다고 생각) 

> git add . -> git commit -m "first commit" -> git push origin 브렌치이름

4. 마스터 브렌치에 소스 가져오기(pull)
> git pull origin master
pull을 하기전에는 기존에 소스코드들을 commit을 먼저 해놔야 한다 

5. 브렌치끼리 이동하는 법
> git checkout 브렌치이름
내가 내 브렌치에서 마스터 브렌치로 이동을 하고 싶거나 다른 브렌치로 이동하고싶으면 해당 명령어를 쓰면 된다
