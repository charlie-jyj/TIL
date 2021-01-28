# git 기본

- workspace

- stage
- repository



## git 시작하기

- `init`
  - $ git init
- `config --global user.name` '이름'
- `config --global user.email '이메일'`



## 변경사항 반영하기

- `add`
- `commit`
- `push`



## 취소하기

- `restore` 
- `reset`
  - commit id를 통해 특정 시점으로 돌아간다.
  - 로컬의 변경 사항이  reset 되지는 않는다. (다소 안전)
  - 기본적으로 local로 돌아간다 (add하면 staging 될 것)
  - -- soft (option) 추가하면 stage로 돌아간다
  -  --hard (option) 추가하면  로컬의 변경 사항도 reset 된다 (위험)



## 용어 살펴보기

### `Branch`

branch를 따서 원본에 새로운 기능을 구현하고 

완성되면 master에 합치고 망했다면 branch를 버린다.

| 명령어 | 내용                          | 예시                             |
| ------ | ----------------------------- | -------------------------------- |
| branch | branch를 생성한다             | $ git branch  <branch name>      |
|        | branch 내역 확인              | $ git branch                     |
| switch | branch로 이동한다(checkout)   | $ git switch  <branch name>      |
|        | 생성하면서 이동               | $ git switch -c  <branch name>   |
| merge  | branch를 통합한다             | $ git merge  <branch name>       |
|        | branch를 삭제한다             | $ git branch -d  <branch name>   |
|        | branch 강제 삭제 (merge 없이) | $ git branch -D  <branch name>   |
| reflog | log + checkout 기록까지       | $ git reflog                     |
| push   | branch를 repo에               | $ git push origin  <branch name> |



1. 생성
2. 전환
3. 작업
4. 전환
5. 병합



### `Master`

branch중 기둥이되는 main 가지에서 가장 최신의 commit

branch를 끌어올 때엔 (=변경 사항을 취합) 

HEAD가 Master로 이동해야 한다.



### `Merge`

branch가 걸은 길을 master가 걷는 것 (Fast-forward)

merge 후에는 branch를 삭제한다 (권장)



####  만약 master에서 수정이 일어났다면? (branch와 다른 길)

##### merge commit

master와 branch를 합친 commit을 새로 만든다.

git log를 찍으면 시간 순으로 볼 수 있다



### `Conflict`

master의 내용과 branch의 내용이 충돌할 경우

직접 수정하며 지울 코드와 남길 코드를 결정한다.



### `HEAD`

'나' 내가 어디에 있나? master? branch?

나의 위치를 표시한다.



### `remote`

듀얼 push를 어떻게 할까?

$ git remote add KEY VALUE

하나일 때는 key를 `origin`으로 정한다.





## 정리

| 명령어  | 내용                    | 예시                              |
| ------- | ----------------------- | --------------------------------- |
| add     | 변경사항 stage로 올리기 | $ git add filename.md             |
| commit  | stage에서 repo로 올리기 | $ git commit -m 'message'         |
| log     | commit 내역 (id) 보기   | $ git log                         |
| status  | 전체 상태 확인          | $ git status                      |
| push    | gitlab으로 업로드       | $ git push origin master          |
| remote  | origin 변경하기         | $ git remote set-url origin [url] |
|         | repo add 하기           | $ git remote add [별칭] [url]     |
| clone   | clone 받기              | $ git clone [url]                 |
|         | 원격지 보기             | $ git remote -v                   |
| pull    | update하기              | $ git pull                        |
|         | 협업자가 pull 받기      | $ git pull origin main            |
| restore | stage에서 내리기        | $ git restore --staged [파일이름] |
| reset   | commit 취소하기         | $ git reset  [commit id]          |



