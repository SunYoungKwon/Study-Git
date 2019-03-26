# Study Git
## 저장소 생성
#### 저장소 생성
```
git init
git init --bare 저장소이름   // 수정없이 저장만 할 저장소 생성, 
```
#### remote저장소 생성
```
git remote add origin '저장소주소'              // 해당 주소로 연결되는 origin이라는 이름의 remote저장소 생성
git remote                                     // 현재 프로젝트에 등록된 remote저장소 목록을 보여줌
git remote -v                                  // remote저장소 목록을 ULR과 함께 보여줌
git remote set-url 저장소이름 새로운저장소주소   // remote저장소의 url
```
## status
#### 현재 파일들의 상태 출력
```
git status
```
- Untracked file: add되기 전. git의 추적을 받지 않는 파일

- modified: 수정된 것
  + Changes to be commited: commit될 것
  + Changes not staged for commit: commit되지 않을 것
## log
```
git log                               // 현재까지 commit한 내용 출력
git log -p                            // 각 commit사이의 소스코드상의 변경사항을 함께 출력
git log diff commitID1..commitID2     // commitID1과 commitID2사이의 변경사항 출력
git log --branch                      // 모든 브랜치를 표현
git log --graph                       // 그래프로 표현 
```
## add
#### 파일을 add하기
```
git add 'File'
git add *        // 모든 파일을 add
git add -u       // modified & deleted 파일만 add
```
#### add 취소하기
```
git reset           // 모든 파일의 add를 취소
git reset 'File'
```
## commit
#### commit하기
```
git commit
git commit -a                    // modified & deleted 파일을 자동으로 add하고 commit
git commit -m 'commit message'   // 에디처를 거치지않고 바로 commit메세지 작성
```
#### commit 취소 하기
```
git reset 버전아이디 --hard   // 작성한 commit아이디 상태로 돌아가고 그 이후의 버전은 버림
git revert 버전아이디         // 버전아이디 커밋을 취소한 내용을 새로운 버전으로 만듦
* push후에는 commit내용을 건드리지 말 것
```
## push
#### Github에 작업물 push
1. Github에 repository생성
2. 작업 후 commit
3. Github에 생성한 ropository주소로 remote저장소 생성
```
git remote add origin 'repository주소'
git remote      // 확인
```
4. 작업물 push
```
git push -u origin master     // local저장소의 브랜치와 원격저장소의 master브랜치 연결. 다음부터 git push만 하면 됨.
```
## pull
#### update내용을 local로 가져오기
```
git pull
```
## branch
```
git branch     // 현재 브랜치목록을 보여줌
```
#### branch 생성, 전환, 삭제
```
git branch nameOfBranch
git checkout master
git branch -d nameOfBranch     // 현재 위치가 삭제할 브랜치여서는 안됨
git branch -D nameOfBranch     // 병합하지 않은 브랜치를 강제 삭제

git checkout -b nameOfBranch   // 새로운 브랜치를 생성하고 생성되 브랜치로 전환
```
#### merge branch
```
git checkout branch1    // branch1으로 이동
gir merge branch2       // branch2를 branch1(현재 위치한 브랜치)에 merge
```
#### branch 충돌 해결
1. CONFLICT 에러 발생
2. git status로 충돌이 일어난 파일 확인
3. 출돌이 일어난 파일 수정
```
<<<<<<< HEAD     // 현재 브랜치
내용1
=======
내용2
>>>>>>> branch   // merge하려던 브랜치
```
4. git add '충돌파일명'
## etc
```
pwd                // 현재 나의 위치
mkdir 폴더명        // 현재 위치에 새로운 폴더 생성
cp file1 file2     // file1과 같은 내용의 fil12를 생성(확장자 쓰기)
git                // 사용할 수 있는 명령어 표시
ls -al             // 현재 디렉토리의 파일 목록 출력
cat 파일명.확장자   // 선택한 파일의 내용을 출력
명령어 --help      // 해당 명령어에 대한 메뉴얼을 보여줌
```
---
## Fork한 repository 최신으로 동기화
1. 원본 repository를 remote저장소로 추가
```
git remote add upstream '원본 저장소 주소'
git remote -v      // 확인
```
2. upstream으로부터 최신 업데이트 가져오기
```
git fetch upstream
```
3. upstream의 master branch로부터 나의 local master branch로 merge
```
git checkout master          // local master branch로 이동
git merge upstream/master
```
4. push하여 origin remote repository에 적용
```
git push origin master
```
