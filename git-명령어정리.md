# git 명령어 목록

1. git init </br>
평범한 폴더를 git 저장소로 초기화시켜 준다.

2. git status </br>
파일이 stage 상태인지 unstage 상태인지 확인한다.

3. git add <파일이름> </br>
<파일이름>을 stage 상태로 만든다.

4. git add . </br>
로컬 저장소의 모든 파일을 stage 상태로 만든다.

5. git commit -m "<커밋 내용>" </br>
<커밋 내용>을 커밋 메시지로 하여 staged된 파일을 기록한다.

6. git log </br>
커밋된 내역을 확인한다.

7. git push origin </br>
로컬에 있는 커밋 사항을 원격 저장소(github)로 전송한다.

8. git pull origin </br>
원격 저장소(github)에 있는 커밋 내역을 로컬로 당겨서 가지고 온다.

9. git commit --amend </br>
마지막 커밋 내역을 수정한다.