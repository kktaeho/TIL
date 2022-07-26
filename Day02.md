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


