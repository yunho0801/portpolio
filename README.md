# Simple Portfolio Website

HTML, CSS, 기본 JavaScript로 만든 2페이지 포트폴리오 웹사이트입니다.

## 구성

- `index.html`: 자기소개 페이지
- `activities.html`: 활동 목록 페이지
- `styles.css`: 반응형 Material UI 스타일
- `script.js`: 모바일 메뉴, 활동 필터, AI 설문 전송 기능

## 실행 방법

1. 이 폴더를 엽니다.
2. `index.html` 파일을 브라우저로 실행합니다.
3. 상단 메뉴에서 소개 페이지와 활동 페이지를 이동합니다.

## 수정 방법

1. `index.html`에서 이름, 소개 문구, 기술 스택을 수정합니다.
2. `activities.html`에서 활동 카드 내용을 수정합니다.
3. `script.js`에서 `makeWebhookUrl` 값을 Make.com Custom Webhook URL로 교체합니다.
   예시 URL 그대로 두면 접수되지 않습니다.
4. `styles.css`에서 색상과 여백을 수정합니다.

## GitHub 업로드 순서

```bash
git init
git config user.name "사용자이름"
git config user.email "이메일주소"
git add .
git commit -m "Add portfolio website"
git branch -M main
git remote add origin 레포지터리주소
git push -u origin main
```

SSH 연결 확인:

```bash
ssh -T git@github.com
```
