# Study Git
## 저장소 생성
#### 저장소 생성
```
git init
git init --bare 저장소이름   // 수정없이 저장만 할 저장소 생성, 
```
#### remote저장소 생성
```
git remote add origin '저장소주소'   // 해당 주소로 연결되는 origin이라는 이름의 remote저장소 생성
git remote   // 현재 프로젝트에 등록된 remote저장소 목록을 보여줌
git remote -v   // remote저장소 목록을 ULR과 함께 보여줌
```
## add
#### 파일을 add하기
```
git add 'File'
git add *   // 모든 파일을 add
```
#### add 취소하기
```
git reset   // 모든 파일의 add를 취소
git reset 'File'
```
## commit
## push
## pull
## branch
## merge
---
## Fork한 repository최신으로 동기화
1. 원본 repository를 remote저장소로 추가
```
git remote add upstream '원본 저장소 주소'
git remote -v   // 확인
```
2. upstream으로부터 최신 업데이트 가져오기
```
git fetch upstream
```
3. upstream의 master branch로부터 나의 local master branch로 merge
```
git checkout master   // local master branch로 이동
git merge upstream/master
```
4. push하여 origin remote repository에 적용
```
git push origin master
```
