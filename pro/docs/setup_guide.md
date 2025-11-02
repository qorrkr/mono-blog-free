# ⚙️ 설치 가이드 (Setup Guide)

이 문서는 블로그 사이트를 처음 설치하고 실행하는 사람을 위한 가이드입니다.  
코딩을 전혀 몰라도 그대로 따라 하면 됩니다.

---

## 🧩 1. 준비물

| 항목 | 설명 |
|------|------|
| 웹 브라우저 | Chrome 또는 Edge 권장 |
| 텍스트 편집기 | VS Code (무료, https://code.visualstudio.com) |
| 깃허브 계정 | 무료 가입: https://github.com |

---

## 🧭 2. 프로젝트 다운로드

1. 페이지 상단의 **“Code” → “Download ZIP”** 클릭  
2. 파일을 내 컴퓨터에 저장하고 압축 해제  
3. 압축을 풀면 `index.html` 파일이 보입니다  
4. 파일을 더블클릭하면 바로 사이트가 열립니다 🚀

> 💡 별도의 설치 프로그램이 필요하지 않아요.  
> 모든 코드는 HTML, CSS, JS만 사용합니다.

---

## 💻 3. 폴더 구조 설명

my-blog/
├─ index.html # 메인 페이지
├─ login.html # 로그인 페이지
├─ post.html # 글 상세 페이지
├─ write.html # 글 작성 페이지
├─ css/
│ ├─ main.css
│ └─ dark.css
├─ js/
│ ├─ main.js
│ └─ auth.js
└─ assets/
├─ logo.png
└─ preview.png

---

## 🌐 4. 배포 방법 (Netlify 기준)

1. [https://www.netlify.com](https://www.netlify.com) 접속  
2. 무료 회원가입 후 “**Add new site → Import an existing project**” 클릭  
3. 깃허브 저장소 연결  
4. Build command → `none`, Publish directory → `/` 입력  
5. “Deploy site” 클릭 → 끝 🎉

---

## 🧠 5. 문제 해결

| 문제 | 원인 | 해결법 |
|------|------|--------|
| 페이지가 안 열려요 | HTML 파일 이름이 바뀌었을 수 있어요 | `index.html` 유지 |
| 스타일이 적용 안돼요 | CSS 경로가 잘못되었어요 | `css/main.css` 확인 |
| 버튼이 작동 안 해요 | JavaScript 경로 누락 | `<script src="js/main.js"></script>` 추가 |

---

> ✅ 이 파일 하나면 누구든 블로그 사이트를 바로 실행할 수 있습니다.
