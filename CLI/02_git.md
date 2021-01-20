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



| 명령어 | 내용                    | 예시                              |
| ------ | ----------------------- | --------------------------------- |
| add    | 변경사항 stage로 올리기 | $ git add filename.md             |
| commit | stage에서 repo로 올리기 | $ git commit -m 'message'         |
| log    | commit 내역 보기        | $ git log                         |
| status | 전체 상태 확인          | $ git status                      |
| push   | gitlab으로 업로드       | $ git push origin master          |
| remote | origin 변경하기         | $ git remote set-url origin [url] |
| clone  | clone 받기              | $ git clone [url]                 |
|        | 원격지 보기             | $ git remote -v                   |
| pull   | update하기              | $ git pull                        |



