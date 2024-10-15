---
title: "[Front-End] JSP와 HTML의 차이, JSP 일반 게시판 리스트"
date: 2024-05-29 19:30:00 +0900
categories:
  - docs
  - jsp
  - html
  - front-end
tags:
  - jsp
  - html
  - board
  - front-end
layout: single
---

# HTML과 JSP의 차이
 - **HTML** : 정적 페이지 - 데이터 변경이 안됨
 - **JSP** : 동적 페이지 - 데이터 변경이 가능하고 DB와 연동이 가능함.

 ## JSP 일반 게시판 리스트
 ```html
<html>
<head>
<metacharset="UTF-8">
<title>일반 게시판 리스트</title>
</head>
<body>
<h1>일반 게시판 리스트</h1>
<!-- JS로 글보기로 페이지 이동
   onclick : click 이벤트 핸들러 속성 -->
<spanonclick="location='view.jsp'">게시글 입니다.</span><br><br>

<!-- a tag : 데이터를 클릭하면 href의 정보를 가져와서 페이지 이동 시킨다. -->
<ahref="writeForm.jsp"><button>등록</button></a>
</body>
</html>
 ```