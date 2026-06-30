# 포트폴리오 웹사이트 만들기

## Step 1. 파일 만들기

아래 4개 파일을 같은 폴더에 둡니다.

```text
index.html
activities.html
styles.css
script.js
```

## Step 2. 자기소개 페이지 만들기

`index.html`은 자기소개, 기술 스택, 연락 버튼을 보여주는 첫 페이지입니다.

```html
<a class="brand" href="index.html">My Portfolio</a>
<a class="active" href="index.html">소개</a>
<a href="activities.html">활동</a>

<h1>안녕하세요, 성장하는 웹 개발자입니다.</h1>
<p>
  사용자에게 편안하고 명확한 경험을 주는 웹사이트를 만들기 위해 HTML, CSS,
  JavaScript를 꾸준히 학습하고 있습니다.
</p>
```

## Step 3. 활동 목록 페이지 만들기

`activities.html`은 프로젝트, 학습, 수상 활동을 카드 형태로 보여줍니다.

```html
<button class="filter-button active" type="button" data-filter="all">전체</button>
<button class="filter-button" type="button" data-filter="project">프로젝트</button>
<button class="filter-button" type="button" data-filter="study">학습</button>
<button class="filter-button" type="button" data-filter="award">수상</button>

<article class="activity-card" data-category="project">
  <div class="activity-icon">01</div>
  <p class="activity-type">Project</p>
  <h2>개인 포트폴리오 웹사이트</h2>
  <p>HTML, CSS, JavaScript로 제작한 반응형 포트폴리오 사이트입니다.</p>
  <span class="activity-date">2026.06</span>
</article>
```

## Step 4. CSS로 Material UI 느낌 적용하기

`styles.css`에서 카드, 버튼, 반응형 레이아웃을 설정합니다.

```css
:root {
  --bg: #f6f8fb;
  --surface: #ffffff;
  --text: #17212b;
  --primary: #1976d2;
  --accent: #00a896;
  --line: #dbe4ee;
  --shadow: 0 14px 36px rgba(19, 35, 53, 0.12);
}

.button.primary,
.filter-button.active {
  background: var(--primary);
  color: #ffffff;
  box-shadow: 0 8px 18px rgba(25, 118, 210, 0.25);
}

@media (max-width: 820px) {
  .hero,
  .split-section {
    grid-template-columns: 1fr;
  }
}
```

## Step 5. JavaScript 기능 추가하기

`script.js`는 모바일 메뉴, 활동 필터, AI 설문 전송 기능을 담당합니다.

```javascript
const menuButton = document.querySelector(".menu-button");
const navLinks = document.querySelector(".nav-links");

if (menuButton && navLinks) {
  menuButton.addEventListener("click", () => {
    const isOpen = navLinks.classList.toggle("open");
    menuButton.setAttribute("aria-expanded", String(isOpen));
  });
}

const filterButtons = document.querySelectorAll(".filter-button");
const activityCards = document.querySelectorAll(".activity-card");

filterButtons.forEach((button) => {
  button.addEventListener("click", () => {
    const selected = button.dataset.filter;

    filterButtons.forEach((item) => item.classList.remove("active"));
    button.classList.add("active");

    activityCards.forEach((card) => {
      const shouldShow = selected === "all" || card.dataset.category === selected;
      card.classList.toggle("is-hidden", !shouldShow);
    });
  });
});
```

## Step 6. AI 설문 서비스 연결하기

Make.com에서 Custom Webhook URL을 발급받은 뒤 `script.js`의 아래 값을 실제 URL로 바꿉니다.

```javascript
const makeWebhookUrl = "https://hook.us1.make.com/your_unique_webhook_id";
```

폼에서 전송되는 데이터 형식은 아래와 같습니다.

```json
{
  "visitor_name": "입력한 이름",
  "visitor_email": "입력한 이메일",
  "visitor_message": "입력한 질문"
}
```

## Step 7. 실행하기

브라우저에서 `index.html`을 열면 웹사이트가 실행됩니다.

## Step 8. GitHub 업로드하기

Git이 설치되어 있고 GitHub 레포지터리가 준비되어 있다면 아래 명령어를 사용합니다.

```bash
git init
git config user.name "사용자이름"
git config user.email "이메일주소"
git add .
git commit -m "Add portfolio website"
git branch -M main
git remote add origin "github 레포지터리 주소"
git push -u origin main
```

SSH 연결 확인:

```bash
ssh -T git@github.com
```
