# 📘 MonoBlog Pro - API Reference

이 문서는 MonoBlog Pro 버전에서 사용되는 주요 API 구조와 데이터 흐름을 설명합니다.
단순 HTML 템플릿이지만, JavaScript fetch()를 통해 LocalStorage 또는 향후 서버(DB)와 통신하는 구조를 기반으로 합니다.

## 🧩 1. 개요 (Overview)

MonoBlog Pro는 프론트엔드 기반 블로그 템플릿입니다.
서버 없이 작동하도록 설계되었으며, 나중에 실제 API 서버와 연동이 가능하도록 구조가 열려 있습니다.

주요 통신 흐름

게시글 저장 → LocalStorage 또는 API 서버

게시글 불러오기 → LocalStorage 또는 API 서버

댓글 등록/삭제 → LocalStorage 또는 API 서버

## 🗂 2. API 구조 (Structure)
### 2-1. 파일별 역할
파일명	역할	비고
main.js	초기화, 페이지 로드, 라우팅 담당	모든 페이지 공통
post.js	게시글 등록 및 불러오기 로직	CRUD 중심
comment.js	댓글 작성/삭제 기능 관리	LocalStorage 기반
auth.js	로그인 및 사용자 인증	현재는 LocalStorage 기반, 향후 DB 연동 가능

## 📄 3. 데이터 포맷 (Data Format)
### 3-1. 게시글 (Post)
```json
{
  "id": "post_1730443901",
  "title": "나의 첫 번째 블로그 포스트",
  "content": "이건 예시 본문 내용입니다.",
  "author": "관리자",
  "createdAt": "2025-10-31T12:00:00Z"
}
```

|필드|타입|설명|
|:---:|:---:|:---:|
|id|String|각 게시글의 고유 ID|
|title|String|게시글 제목|
|content|String|게시글 본문 내용|
|author|String|작성자 이름|
|createdAt|String|(ISO8601)	작성 시각|

### 3-2. 댓글 (Comment)
```json
{
  "id": "cmt_1730443901",
  "postId": "post_1730443901",
  "author": "홍길동",
  "content": "좋은 글이네요!",
  "createdAt": "2025-10-31T12:30:00Z"
}
```

|필드|타입|설명|
|:---:|:---:|:---:|
|id|String|댓글의 고유 ID|
|postId|String|어떤 게시글에 달린 댓글인지 표시|
|author|String|작성자 이름|
|content|String|댓글 내용|
|createdAt|String|(ISO8601)	작성 시각|

## 💾 4. API 예시 (Example)

현재 버전은 LocalStorage 기반으로 작동하지만,
나중에 fetch()를 통해 백엔드와 통신하도록 쉽게 확장할 수 있습니다.

게시글 저장 (Save Post)
```json
function savePost(post) {
  const posts = JSON.parse(localStorage.getItem("posts")) || [];
  posts.push(post);
  localStorage.setItem("posts", JSON.stringify(posts));
}
```

게시글 불러오기 (Get Posts)
```json
function getPosts() {
  const posts = JSON.parse(localStorage.getItem("posts")) || [];
  return posts;
}
```

댓글 등록 (Add Comment)
```json
function addComment(comment) {
  const comments = JSON.parse(localStorage.getItem("comments")) || [];
  comments.push(comment);
  localStorage.setItem("comments", JSON.stringify(comments));
}
```

## 🧠 5. 향후 확장 (Future API Integration)

MonoBlog Pro는 추후 Firebase, Supabase, Express.js, or Node.js 서버와 연동할 수 있도록 설계되었습니다.

예를 들어, Firebase 연동 시 다음과 같은 코드로 전환할 수 있습니다.
```json
// 기존 LocalStorage 저장 → Firebase 저장으로 변경
import { db } from "./firebase.js";
import { addDoc, collection } from "firebase/firestore";

async function savePostToFirebase(post) {
  await addDoc(collection(db, "posts"), post);
}
```

## 🧭 6. 요약
항목	설명
기본 저장소	LocalStorage
확장 가능성	Firebase / Supabase / Node.js
인증 구조	LocalStorage 기반 (이후 JWT 가능)
CRUD 기능	게시글, 댓글 전부 포함
배포 환경	GitHub Pages, Netlify 완벽 호환
