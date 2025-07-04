
# Git 명령어 정리

## 기본 설정

```bash
git init
```
- 깃 초기화를 통해 로컬 레포지토리 생성

```bash
git config user.name "이름"
git config user.email "이메일"
```
- 깃 사용자 설정 작업

---

## 커밋 작업 흐름

```bash
git add [파일명]
```
- 수정한 파일을 스테이징하는 작업

```bash
git commit -m "[커밋 메시지]"
```
- 커밋에 대한 요약 메시지 작성
- `-m` 옵션을 생략하면 에디터 창이 열림

```bash
git reset [파일명]
```
- 스테이징된 파일을 스테이징 취소

---

## 원격 저장소 관련

```bash
git push [원격레포명] [브랜치명]
```
- 스테이징된 파일을 원격 저장소에 업로드

```bash
git pull [원격레포명] [브랜치명]
```
- 원격 저장소의 변경사항을 로컬로 가져옴

```bash
git clone [원격 레포 주소]
```
- 원격 레포를 로컬에 복제 (빈 디렉토리에서 진행 권장)

---

## 커밋 히스토리 확인

```bash
git log [옵션]
```
- 커밋 기록 확인
- `--pretty=oneline` : 한 줄로 출력
- `--pretty=short` : 요약 출력

```bash
git show [커밋ID]
```
- 특정 커밋에 대한 변경사항 확인

```bash
git diff [이전커밋ID] [최근커밋ID]
```
- 두 커밋 간의 차이점 확인

---

## 커밋 롤백 및 변경

```bash
git reset --hard [커밋ID]
```
- 해당 커밋 시점으로 강제 되돌림

```bash
git revert [커밋ID]
```
- 해당 커밋을 취소하는 새로운 커밋 생성

```bash
git reset [커밋ID]
```
- 해당 커밋 시점으로 돌아감 (새 커밋 생성 없이)

---

## 브랜치 관련

```bash
git branch [브랜치명]
```
- 새 브랜치 생성

```bash
git branch -d [브랜치명]
```
- 브랜치 삭제

```bash
git checkout [브랜치명]
```
- 브랜치 전환

```bash
git checkout -b [브랜치명]
```
- 새 브랜치 생성 후 바로 전환

```bash
git status
```
- 현재 브랜치 상태 확인

---

## Push 단축 명령어

```bash
git push --set-upstream origin [브랜치명]
```
- 이후에는 `git push`만 입력해도 자동 푸시 가능

```bash
git push origin [브랜치명]
```
- 특정 브랜치로 푸시 (저장)

---

## 원격 저장소 변경사항 확인

```bash
git fetch
```
- 원격 저장소 변경사항 확인 (로컬로는 가져오지 않음)
- origin/~브랜치 생성되서 확인 가능

---

## 기타 유용한 명령어

```bash
git blame [파일명]
```
- 각 라인의 작성자 및 커밋 기록 확인

```bash
git rebase [브랜치명]
```
- 브랜치를 병합하되 커밋 히스토리를 정리하면서 진행

```bash
git cherry-pick [커밋ID]
```
- 해당 커밋을 현재 브랜치에 적용

```bash
git stash
git stash list
git stash drop
```
- 현재 작업 내용을 임시 저장, 목록 보기, 삭제

---

## HEAD란?

- 현재 체크아웃된 브랜치 또는 커밋을 가리키는 포인터
- 현재 로컬에서 작업 중인 커밋을 참조함

---

## Conflict 해결 방법

- `git pull` 시 충돌이 발생하면, 충돌된 파일을 수동으로 수정하거나
- 충돌 원인 개발자에게 문의하여 해결
