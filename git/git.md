1. 현재 디렉토리를 Git이 관리하는 프로젝트 디렉토리(=working directory)로 설정하고 그 안에 레포지토리 (.git 디렉토리) 생성
    - git init
    - .git이 Repository
    - Version 관리

2. Git에게 commit한 사람 알려주기! (이름, 이메일)
    - git config user.name "juju199a"
    - git config user.email "juju199a@gmail.com"

3. 커밋할 파일을 미리 지정해줘야 함 (add)
    - git add calculator.py
    - git add License

4. 커밋 메시지 남기기 (옵션 -m)
    - git commit -m "Create calculate.py and License"

5. 현재 상태 보기
    - git status
    - stage: git add로 파일을 staging area에 추가하는 것

6. Staging Area 에서 파일 제거
    - git reset
    - git status
    - clean: 이전 커밋 이후로 **변경사항 없음!**

7. 사용법 알기
    - git help

8. 원격 레포지토리 or 리모트 레포지토리
    - git remote add origin https://github.com/juju199a
    - git push -u origin master

9. 로컬 레포지토리 -> 리모트 레포지토리
    - git push
    - 로컬 레포지토리의 내용을 처음으로 GitHub의 리모트 레포지토리로 보낼때
    - git push --set-upstream otigin master

10. 리모트 레포지토리 -> 로컬 레포지토리
    - git pull

11. Explorer > numpy 검색 > Code > 주소 복사
    - cd ..
    - git clone https://github.com/numpy/numpy.git
    - cd numpy

12. Commit 히스토리 (로컬 레포지토리)
    - git log
    - q 
    - git log --pretty=oneline

13. 어떤 파일이 어떻게 변했는지 알고 싶을 때 (로컬 레포지토리)
    - git show 4af1

14. git add .
    - git commit
    - i > Add One function > :wq!
    - git log
    
15. 커밋 메시지 수정 (로컬 레포지토리)
    - git log --pretty=oneline
    - 소스 수정 > 저장
    - git add .
    - git commit --amend
    - i > Add multiply function
    - git log --pretty=oneline
    - git push

16. Aliasing
    - git config alias.history "log --pretty=oneline"
    - git history

17. 비교
    - git history
    - git diff facd eea5

18. 최근에 한 것을 가리킴
    - git history
    - **HEAD: 보통 가장 최근에 한 커밋을 가리킴**

19. **HEAD가 과거의 커밋을 가리키게 할 수 있다!**
    - git reset --hard eea5
    - git history
    - working directory의 내용도 과거 커밋의 모습으로 돌아가게 한다!

20. **--hard는 다 사라짐**
    - option / working directory / staging area / local repository
    - --soft / 안 바뀜 / 안 바뀜 / HEAD가 과거 가리킴
    - --mixed / 안 바뀜 / 과거 바뀜 / HEAD가 과거 가리킴
    - --hard / 과거 바뀜 / 과거 바뀜 / HEAD가 과거 가리킴

21. git reset --soft 옵션
    - git add .
    - git status //스테이징 파일 확인
    - git history
    - git reset --soft 4af1
    - git history //로컬 레포지토리 확인
    - git status //스테이징 확인

22. git reset --mixed 옵션
    - git reset --mixed facd
    - git history //로컬 레포지토리 확인
    - git status //스테이징 확인

23. git reset --hard  옵션
    - git reset --hard -33cd
    - git history //로컬 레포지토리 확인
    - git status //스테이징 확인

24. 태그달기
    - git tag [태그이름] [커밋아이디]

