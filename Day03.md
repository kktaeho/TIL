# 오늘 배운 내용 작성

## 공동작업 Github Fork
1. 흐름도
- 원본 원격(origin) --fork--> 내 원격 저장소(branch)  --clone--> 로컬 저장소()
- 원본 원격(origin) --git remote add upstream <원본 주소>--> 로컬 저장소()
- 원본 원격(origin) <--Pull request-- 내 원격 저장소(branch)  <--push-- 로컬 저장소()
- 원본 원격(origin) --pull--> 로컬 저장소() (병합으로 변경된 원본 원격저장소 master를 로컬로 받아오며 기존 로컬 브랜치는 삭제(kktae))
2. 상세
- 상대방 Github 폴더에 접속하여 Fork 누르게 되면 나의 Github 폴더에 동기화된다.
- 원격 저장소에 저장된 폴더를 로컬 저장소에 저장  git clone <내 주소>
- 로컬 저장소와 원본 원격 저장소 동기화 git remote add upstream https://github.com/edukyle/TIL-remote.git 처럼 입력해주면 연동된다. (원본 원격 저장소는 보통 upstream이라고 사용)
- 다음으로 그냥 사용하는 것이 아닌 브랜치를 생성하여 작업을 진행한다  git switch -c kktae  (kktae 브랜치만들고 이동하라는 뜻)
- 기능 구현이 되었다면 git push origin kktae (내 원격 저장소에 브랜치 올림)
- github에서 pull request를 통해 원격 저장소 브랜치origin을 원본 원격 저장소에 반영해달라고 요청
- 브랜치가 병합되면 원격 저장소의 브랜치는 삭제하며 로컬에서는 master브랜치로 이동 git switch master
