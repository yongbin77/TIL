## <branch 사용 이유>


1. 동시 작업을 위해

> 팀원 A,B,C가 있을경우, 세명이 각각 branch를 만들은 후,
자신의 branch에 각각 맡은 부분의 개발을 진행.
그 후, merge를 통해 자신이 맡은 부분의 코드를 master에 합치거나,
branch끼리 merge를 통해 코드를 합쳐줌.


쉽게 설명하자면,
자신이 맡은 부분의 작업을 각자의 branch에서 동시에 진행할 수 있다.
그리고 merge 를 통해 나중에 코드 합치기도 편하기 때문에 사용한다.


 
2. 프로젝트 관리를 위해

> 큰 프로젝트를 진행하거나, 여러명이서 협업을 진행할 경우, 
만약 master안에서 작업을 진행하게되면,
코드가 꼬일경우, master안의 전체 프로젝트를 다시 검토하여 복구해야되므로 비효율적.
하지만 각자의 branch안에서 맡은부분을 수행할 경우,
코드가 꼬였을 경우 , 그 branch에서 작업한 부분만 다시 재검토하면 되기 때문에 효율적임.


쉽게 설명하자면, 
A, B, C 세명이 각각 1번, 2번, 3번 branch에서 작업을 진행함. 
A가 작업중, 코드가 꼬였어도 master에서 진행한게 아니고 자신의 branch인
1번 branch에서 작업을 한 것이므로, 1번 branch만 검토하면됨. 
그리고 B, C는 A와 상관없이 자신의 코드에 문제가 없으면 master에 merge요청을 하면됨.


 
 <결론>
> 협업시, 매우 효율적으로 작업을 진행할 수 있음.

<기본적인 branch 명령어 총정리>
1. branch 생성 및 생성된 branch로 전환
git checkout -b <branch 이름>
*<branch 이름> 에는 자신이 원하는 이름을 넣어주면 된다.

2. 현재 자신의 파일과 연결된 branch 목록
git branch
 
3. branch전환
git checkout <branch 이름>
*존재하는 branch이름을 적어야됨.
 
4. branch 생성
git branch <branch 이름>
 
5. branch 삭제
git branch -d <branch 이름>
 
6. branch 강제 삭제
git branch -D <branch 이름>
*이 branch가 정말 필요 없는데, "git branch -d <branch 이름>"으로는 삭제가 안될경우 이용.
 
7. branch에 코드push
git push origin <branch 이름>
 
8. merge하는 법
git checkout <branch 이름>
git merge <branch 이름>
 
 
예제 1) master에다가  A라는 branch를 merge하고 싶으면, 
git checkout master
git merge A
 
예제2) B라는 branch에다가 C라는 branch를 merge하고 싶다면,
git checkout B
git merge A

9. 다른 branch로 이동
git checkout <branch 이름>
