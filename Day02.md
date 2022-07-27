# 오늘 배운 내용 작성

## Clone, Pull, 공유파일
- git clone <주소> 형식으로 github에 있는 데이터를 복제해 가져온다.
- 파일 수정후 git add . , git commit -m "이름" 을 통해 업로드할 준비
- git push origin master 라는 <저장소 이름><브랜치 이름> 작성하면 github 업로드

### 파일 생성 후 git 업로드
```bash
# TIL-home

$ git init
$ touch day1.md
$ git add .
$ git commit -m "집에서 Day1 작성"
$ git remote add origin https://github.com/edukyle/TIL-remote.git
$ git push origin master
```
### github에서 내려받기
```bash
# TIL-class

$ git clone https://github.com/edukyle/TIL-remote.git TIL-clas
```

### 내려받은 파일 수정후 업로드

```bash
# TIL-class

$ touch day2.md
$ git add .
$ git commit -m "강의장에서 Day2 작성"
$ git push origin master
```

# 다시 업로드한 파일 내려받기

```bash
# TIL-home

$ git pull origin master
```
- 이 작업이 반복된다.

## Branch, Branch-merge
- 브랜치를 통해 원본에 지장없이 작업이 가능하다.

### 브랜치 조회, 생성, 삭제 등 브랜치와 관련된 Git 명령어

```bash
# 브랜치 목록 확인
$ git branch

# 원격 저장소의 브랜치 목록 확인
$ git branch -r

# 새로운 브랜치 생성
$ git branch <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성
$ git branch <브랜치 이름> <커밋 ID>

# 특정 브랜치 삭제
$ git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
$ git branch -D <브랜치 이름> # (주의) 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
```

### 브랜치의 head(현재 브랜치를 가르키는 포인터) 이동하는 명령어

```bash
# 다른 브랜치로 이동
$ git switch <다른 브랜치 이름>

# 브랜치를 새로 생성과 동시에 이동
$ git switch -c <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성과 동시에 이동
$ git switch -c <브랜치 이름> <커밋 ID>
```
- git switch 하기 전에, 해당 브랜치의 변경 사항을 커밋 하셨나요?

master 브랜치와 feature 브랜치가 있다고 가정해보겠습니다.
feature 브랜치에서 test.txt를 만들고 git commit 하지 않은 상황에서
master 브랜치로 이동하게 되면, test.txt 파일이 그대로 남아있습니다.

따라서 브랜치를 이동하기 전에, 꼭 커밋을 완료하고 이동하도록 합니다.
> 브랜치에서는 origin master 안하는 이유가 master는 본서버이기 때문에 작동 중인 서비스의 에러를 방지하고자 사용하지 않는다