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

12. Commit 히스토리
    - git log
    - q 
    - git log --pretty=oneline

13. 어떤 파일이 어떻게 변했는지 알고 싶을 때
    - git show 4af1

14. git add .
    - git commit
    - i > Add One function > :wq!
    - git log

15. 커밋 메시지 수정
    - git log --pretty=oneline
    - 소스 수정 > 저장
    - git add .
    - git commit --amend
    - i > Add multiply function
    - git log --pretty=oneline
    - git push
    

