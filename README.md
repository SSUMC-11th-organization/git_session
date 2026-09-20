# 🚀 GitHub Session

Git과 GitHub의 기본 사용법을 실습합니다.

---

## ⚙️ 1. Git 최초 설정

Git을 처음 설치했다면 이름과 이메일을 설정합니다.

```bash
git config --global user.name "민스"
git config --global user.email "mins@soongsil.ac.kr"
```

설정 확인:

```bash
git config --global --list
```

---

# 💻 1부. Local Git

## 🌱 2. Git 시작하기

실습할 폴더를 만들고 VS Code로 엽니다.

```bash
git init
```

현재 폴더의 버전 관리를 시작합니다.

현재 Git 상태를 확인합니다.

```bash
git status
```

파일을 만든 직후와 `git add` 이후에 실행하여,
새로 생긴 파일 / 수정된 파일 / Commit 대기 중인 파일을 확인합니다.

---

## ➕ 3. 파일 추가 및 Commit

파일을 만들거나 수정한 뒤 Staging Area에 추가합니다.

```bash
git add 파일명
```

현재 폴더의 변경 파일을 모두 추가하려면:

```bash
git add .
```

Commit을 생성합니다.

```bash
git commit -m "커밋 메시지"
```

기본 흐름:

```text
Working Directory
        ↓ git add
Staging Area
        ↓ git commit
Local Repository
```

---

## 🔍 4. Commit 기록 확인

```bash
git log --all --oneline
```

브랜치 구조까지 확인하려면:

```bash
git log --all --oneline --graph
```

---

## 📝 5. 변경 내용 확인

아직 `git add`하지 않은 변경 내용을 확인합니다.

```bash
git diff
```

`git add`한 변경 내용을 확인하려면:

```bash
git diff --staged
```

VS Code의 **Git Graph** 확장 프로그램을 사용하면 Commit과 Branch 흐름을 시각적으로 확인할 수 있습니다.

---

## 🖥️ 6. VS Code Source Control

VS Code 왼쪽의 **Source Control** 메뉴에서도 Git을 사용할 수 있습니다.

- `+` 버튼 → `git add`
- Commit 버튼 → `git commit`
- 변경된 파일 확인

---

## 🌿 7. Branch 만들기

브랜치 생성:

```bash
git branch develop
```

브랜치 이동:

```bash
git switch develop
```

브랜치 확인:

```bash
git branch
```

---

## 🔀 8. Merge

합칠 기준 브랜치로 이동합니다.

```bash
git switch main
```

다른 브랜치를 합칩니다.

```bash
git merge develop
```

충돌이 발생하면 파일을 수정한 뒤 Merge Commit을 완료합니다.

```bash
git add .
git commit
```

---

## ↩️ 9. 되돌리기

### 파일 수정 취소

마지막 Commit 상태로 파일을 되돌립니다.

```bash
git restore 파일명
```

### Commit 되돌리기

먼저 Commit ID를 확인합니다.

```bash
git log --all --oneline
```

특정 Commit 상태로 되돌립니다.

```bash
git reset --hard <커밋ID>
```

`--hard`는 이후 작업 내용까지 삭제될 수 있으므로 주의해서 사용합니다.

참고:

- `--soft` : Commit만 되돌리고 변경 내용은 Staging Area에 남김
- `--mixed` : Commit과 Staging을 되돌리고 변경 내용은 Working Directory에 남김
- `--hard` : Commit, Staging, Working Directory의 변경 내용을 모두 되돌림

### 기존 Commit을 남겨두고 취소

```bash
git revert <커밋ID>
```

---

# :octocat: 2부. GitHub

## ⬆️ 10. Local Repository를 GitHub에 Push

GitHub에서 새 Repository를 만듭니다.

원격 저장소 주소를 직접 사용해서 Push할 수도 있습니다.

```bash
git push <원격저장소주소> main
```

원격 저장소 주소를 `origin`이라는 이름으로 등록하면 이후 명령어를 간단하게 사용할 수 있습니다.

```bash
git remote add origin <원격저장소주소>
```

연결 확인:

```bash
git remote -v
```

처음 연결할 때:

```bash
git push -u origin main
```

`-u`로 원격 브랜치를 연결해두면 다음부터는 간단하게 사용할 수 있습니다.

```bash
git push
```

---

## 📥 11. Clone

이미 GitHub에 존재하는 Repository를 처음 내 컴퓨터로 가져올 때 사용합니다.

```bash
git clone <원격저장소주소>
```

`git clone`을 하면 Git 저장소 정보와 `origin`도 함께 설정되므로 `git init`과 `git remote add origin`을 다시 할 필요가 없습니다.

---

## 🔄 12. Pull

원격 저장소에 내가 가지고 있지 않은 새로운 Commit이 있다면 바로 Push할 수 없습니다.

원격의 변경 내용을 현재 Branch에 먼저 가져옵니다.

```bash
git pull
```

그다음 다시 Push합니다.

```bash
git push
```

---

# 🤝 3부. UMC Git 협업 실습

지금까지 배운 내용을 활용해 자기소개 파일을 추가하고 GitHub 협업 흐름을 실습합니다.

## 📦 13. UMC Repository Clone

실습 Repository를 내 컴퓨터로 가져옵니다.

```bash
git clone https://github.com/SSUMC-11th-organization/git_session.git
cd git_session
```

---

## ✨ 14. Issue 만들기

GitHub에서 **Git Session 실습** Issue 템플릿을 선택해 Issue를 생성합니다.

- Assignee: 본인
- Label: 실습에 맞는 Label 선택
- 생성된 Issue 번호 확인

---

## 🔄 15. 개인 Main Branch 최신화

자신의 개인 Main Branch로 이동한 뒤 원격의 최신 내용을 가져옵니다.

```bash
git switch 닉네임/main
git pull
```

---

## 🌿 16. 작업 Branch 생성

개인 Main Branch를 기준으로 Issue 번호가 포함된 작업 Branch를 생성합니다.

```bash
git branch 닉네임/#이슈번호
git switch 닉네임/#이슈번호
```

`닉네임`과 `#이슈번호`에는 본인의 닉네임과 실제 Issue 번호를 입력합니다.

---

## 👋 17. 자기소개 파일 작성

`members/example.md`의 형식을 참고해 `members/닉네임.md` 파일을 새로 만들고 자기소개를 작성합니다.

`example.md`는 예시 파일이므로 직접 수정하지 않습니다.

---

## 💾 18. Add 및 Commit

변경 사항을 Staging Area에 추가합니다.

```bash
git add .
git status
```

`git status`에서 자기소개 파일이 Commit 대기 상태인지 확인한 뒤 Commit합니다.

```bash
git commit -m "자기소개 추가"
```

---

## ⬆️ 19. 작업 Branch Push

작업 Branch를 처음 Push하면서 원격 Branch와 연결합니다.

```bash
git push -u origin 닉네임/#이슈번호
```

---

## 🔀 20. Pull Request

GitHub에서 Pull Request를 생성하고 PR 템플릿을 작성합니다.

```text
base    : 닉네임/main
compare : 닉네임/#이슈번호
```

- 관련 Issue 연결
- Reviewer 지정
- Assignee에 본인 지정
- Label 선택
- PR 생성 후 Files changed 확인

---

## 👀 21. Code Review 및 Approve

다른 스터디원의 PR을 확인하고 간단한 Review를 남깁니다.

수정할 내용이 없다면 **Approve** 합니다.

---

## 🎉 22. Merge

Code Review와 Approve를 확인한 뒤 PR을 Merge합니다.

Merge가 완료되면 작업에 사용한 Branch를 삭제합니다. 개인 Main Branch는 삭제하지 않습니다.
