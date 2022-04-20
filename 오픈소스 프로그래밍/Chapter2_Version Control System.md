# Ch2. Version Control System

## 2.1 Dealing with Change

+ 작업물을 어떻게 관리할 것인가?
  - 이미 있는 코드 수정
  - 작업하는 코드 백업
  - 아이디어 있을때 체크
  - 그룹 프로젝트에서 코드 공유
  
+ 단점
  - 누가 카피해 가는것
  - 전체 디렉토리 무단도용
  
+ **그래서, 자동으로 프로세스를 관리해 보자!**
  - Version Control System 으로 관리가 가능하다. 
  - Code Base(문서, Build Tool, Config File, Code  등등)을 관리 가능하다.
  

** Version Control System 장점 5가지
    - 소스코드가 바뀔 때마다의 바뀐 부분을 체크하고 관리할 수 있다.
    - 변경사항을 추적할 수 있다.
    - 필요시 이전 버전으로 롤백 가능
    - 팀 멤버들과 병렬적으로 협업가능
    - 테스트와 배포 과정에서 자동화

** git 명령어 : 
    - git clone : 클론
    - git log : 커밋 로그 내역 보기(종료 : q)
    - git merge : 두 개로 나뉘어졌던 코드 하나로 합치는 것. 
    - git rebase : 두 개로 합치는데, 어느 한쪽을 새로운 나뭇가지로 해서 아예 base를 한쪽으로 한
                   새로운 가지를 뻗게 하는 것.. (새로 정리)
     -git commit -m "" : 커밋
     -git push origin master : 푸시
     -git branch ~~ : 새로운 브랜치 개설
     -git branch --all : 모든 브랜치 목록 보기. 그중에서도 현재 브랜치 어떤 것인지 표시해준다
     -git checkout ~~ : ~~ 브랜치로 이동
               
