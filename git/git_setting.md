# Git 시작하기

## 1. Git 설치 확인

```bash
git --version
```

만약 설치가 안됐다면

```bash
brew install git
```

## 2. 사용자 이름 & 이메일 설정 (최초 1회)

```bash
git config --global user.name "name"
git config --global user.email "my_email@example.com"
```

`설정 확인`:

```bash
git config --global --list
```

## 3. GitHub 계정과 연동 (SSH 권장)

1. SSH 키 생성

```bash
ssh-keygen -t ed25519 -C "my_email@example.com"
```

Enter 연타 -> ~/.ssh/id_ed25519 로 키가 생성됨

2. 공개키 GitHub에 등록

```bash
cat ~/.ssh/id_ed25519.pub
```

출력된 키를 복사해서 GitHub →
https://github.com/settings/keys
→ New SSH key → 붙여넣기 → 저장

3. 연결 테스트

```sh
ssh -T git@github.com
```

성공하면
Hi username! You’ve successfully

## .gitignore

```bash
touch .gitignore
```

.gitnore
node_modules/ (폴더)
.env (파일)
dist/ (폴더)
