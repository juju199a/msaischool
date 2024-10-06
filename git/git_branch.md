1. git status
    - On branch master: **마스터 브랜치** 위에 있다.

2. git branch preminum
    - 브랜치 만듦

3. **git checkout preminum**
    - preminum 다른 브랜치로 이동
    - Free -> Preminum
    - git add .
    - git commit -m "Change License from free to preminum"

4. git branch
    - 현재 브랜치 모두 출력
    - git branch test
    - git branch
    
5. **git branch -d test**
    - 브랜치 삭제 (Delete)

6. git checkout -b test
    - 브랜치로 만들고 바로 이동 (branch)
    - checkout: 다른 branch로 이동
    - branch 생성 + 이동

7. **git merge master**
    - 현재 위치인 preminum branch에 master branch를 합치겠다.
    - git checkout master
    - 소수 수정 > Save
    - git add .
    - git commit -m "Add divide function"
    - git checkout premium

8. Conflict 발생시 해결 방법
    - devide_preminum 함수 이름 수정
    - git add .
    - git commit -m "Change divide function as preminum"
    - devide_free 함수 이름 수정
    - git add .
    - git commit -m "Change divide function as free" >> 잘 됨
    - git merge master >> Conflict
    - git add .
    - git commit
    - commit message 작성
    - :wq
    - 해결

9. 머지 취소
    - git merge --abort
    - 버리다, 취소하다.

10. git remote add origin https://github.com/kyuri-dev/Math_Box.git
    - add는 새로운 리모트 레포지토리를 등록하겠다.
    - 리모트 레포지토리 이름을 origin이라는 이름으로 등록하겠다. 
    - Git에서는 리모트 레포지토리를 최초로 추가할 때 origin이라는 이름으로 가리키는 것이 관례화 되어 있다.
    - "근원, 기원"

11. 트랙킹 정보 설정
    - **git push -u origin master**
    - 현재 로컬 레포지토리에 있는 master 브랜치의 내용을 origin이라는 리모트 레포지토리로 보낸다는 뜻입니다.
    - **이때 같은 이름의 브랜치로 전송하게 되는데 만약 origin이라는 리모트 레포지토리에 master 브랜치가 없으면 master 브랜치를 생성하고 푸시합니다.**
    - -u 는 **--set-upstream** 이라는 옵션의 약자
    - origin에 있는 master 브랜치를 tracking(추적)하는 걸로 설정됩니다.
    - **tracking이라는 건 로컬 레포지토리의 한 브랜치가 리모트 레포지토리의 한 브랜치와 연결되어 그것을 계속 바라보는 상태가 되는 것**
    - 만약에 하지 않는다면, git push origin master:master를 일일이 해 줘야 한다.
    - origin은 리모트 레포지토리를 나타내고,
    - master:master에서 더 먼저 나오는 master는 로컬레포지토리의 master 브랜치 / 더 뒤에 나오는 master는 리모트 레포지토리의 master브랜치를 나타냅니다.

12. 리모트 레포지토리로 master, preminum 올리기
    - git checkout master
    - git push
    - git history
    - git checkout premium
    - git push >> 에러 발생 >> 맨 처음 push 할 때, --set-upstream으로 트랙킹 정보가 설정된다.
    - **git push --set-upstream origin premium** > 리모트 레포지토리에도 preminum 브랜치가 생긴다.

13. HEAD -> master -> 다섯번 째 커밋
    - git checkout master
    - git history
    - HEAD: 어떤 커밋 하나를 가리킴
    - branch: 하나의 코드 관리 흐름 -> 포인터
    - HEAD가 가리키는 commit의 내용대로 working directory의 내용물이 바뀐다.

14. git checkout premium
    - 다른 브랜치로 가는 명령어
    - HEAD가 가리키는 브랜치를 변경하는 작업일 뿐이다.

15. git checkout master
    - HEAD는 master 브랜치를 가리킨다.
    - 다섯번째 커밋대로 워킹 디렉토리로 바뀐다.

16. 새로운 커밋 (일곱번째 커밋)
    - 분기한다.

17. 머지 커밋
    - HEAD > master 인 상태에서
    - git merge premium 하면, 새로운 커밋이 만들어진다.
    - **헤드**가 가리키던 커밋에 **다른 브랜치가 가리키던** 커밋을 합쳐서 **새로운 커밋**을 만든는 작업

18. **git checkout 9033**
    - **Detached HEAD**
    - ~로부터 떨어진, 분리된
    - 과거의 특정 커밋에서 새로운 브랜치를 만들고 싶을 때입니다.
    - git branch premium
    - git checkout premium (Detached HEAD 상태 -> HEAD가 브랜치를 가리키는 정상적인 상태)

18. git checkout master
    - git checkout [가고 싶은 브랜치 이름]
    - = master 브랜치로 이동하라
    - = HEAD가 master 브랜치를 가리키도록 하라
    - = HEAD가 master 브랜치가 가리키던 커밋을 간접적으로 가리키게 됨으로써
    - = working directory의 내부도 그 커밋에 맞게 변함으로써
    - = master 브랜치로 이동하는 것을 사용자는 실감하게 됨

19. git reset vs git checkout
    - git reset / git checkout
    - HEAD가 가리키던 브랜치가 다른 커밋을 가리키도록 한다. / HEAD 자체가 다른 커밋이나 브랜치를 가리키도록 한다.
    - HEAD도 결국 간접적으로 다른 커밋을 가리키게 되는 효과가 생긴다. / 브랜치를 통하지 않고, 커밋을 직접적으로 가리키는 HEAD를 Detached HEAD라고 한다.

20. 정리
    - git branch [새 브랜치 이름]: 새로운 브랜치를 생성
    - git checkout -b [새 브랜치 이름]: 새로운 브랜치를 생성하고 그 브랜치로 바로 이동
    - git branch -d [기존 브랜치 이름]: 브랜치 삭제
    - git checkout [기존 브랜치 이름]: 그 브랜치로 이동
    - **git merge [기존 브랜치 이름]**: 현재 브랜치에 다른 브랜치를 머지
    - git merge --abort: 머지를 하다가 conflict가 발생했을 때, 일단은 머지 작업을 취소하고 이전 상태로 돌아감

