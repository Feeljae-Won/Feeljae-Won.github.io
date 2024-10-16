---
title: "[Front-End] CSS 선택자, Layout"
date: 2024-06-04 19:00:00 +0900
categories:
  - docs
  - css
  - front-end
tags:
  - css
  - layout
  - selector
  - front-end
layout: single
---
# CSS 선택자
## 선택자 {스타일 항목 : 스타일 값; ...}
   - **기본 선택자** 
      - `a` : `<a>` 태그를 선택
      - `.a` : `class="a"` `a`라는 `클래스`를 가진 모든 태그
      - `#a` :  `id="a"` `a`라는 `ID`를 가진 태그. **한 문서에 아이디가 중복될 경우 처음 1개만 적용.**
   - **다수 선택자**
      - `,`로 선택.
         ```css
         a, #a, .a {

         }
         ```
   - **상태 선택자**
      - `:`, `:hober` : 마우스가 올라갔을 때. `a:hover` - 앵커 태그 위에 마우스가 올라갔을 때
   - **선택의 상속**
      - `a .data` : `<a>` 태그 안에 `data` class의 태그를 찾는다.

# Layout
```css
   <styletype="text/css">
   /* select(태그를 선택) {syle 지정 -> key:value ; key:value ;}*/
   div{
      border: 1px solid black;
   }
   body {
      margin: 0;
      border : 1px dotted orange;
   }
   .container {
      width: 900px;
      margin: 0 auto;
   }
   h1{ /* h1 태그는 박스이면 허용되는 맨 왼쪽부터 맨 오른쪽까지 차지하는 태그 */
      border: 1px dashed #444;
      /* 박스 범위의 글자 정렬을 가운데로 */
      text-align: center;
   }
   #header, wrap, footer {
      /* width: 800px; /* 테두리 안쪽의 너비 */
      /* 반드시 width가 지정이 되어 있는 상태 창이 박스 태그 보다 더 커야 한다. - 가운데 정렬 */
      /* margin: 0 auto; */
   }
   #header {
      background: red; /* 배경색 */
   }
   #wrap, #aside {
      /* 너비가 800px인 wrap 안에 데이터가 800px가 넘어가면 숨기자(표시하지 않는다.)
         text인 경우는 줄바꿈이 된다. 이미지나 박스 스타일의 너비가 800px를 넘는 경우 숨긴다. */
      overflow: hidden;
   }
   #aside {
      width: 200px;
      background: blue;
      /* 흘러가는 속성 왼쪽 - 오른쪽에 다른 객체가 올수 있도록 허용해준다.
         흘러가는 속성을 무시 시키는 속성 clear: both;
       */
      float: left;
   }
   #content {
      background: green;
   }
   </style>
```
```html
<html>
<head>
<meta charset="UTF-8">
<title>Layout</title>
</head>
   <body>
   <div class="container">
      <!-- 주메뉴 부분 / 로그인 처리 / 로그 -->
      <div id="header">
         <h1>#header 태그</h1>
      </div>
      <!-- 본문 내용 -->
      <div id="wrap">
         <div id="aside">
            <h1>#aside 태그</h1>
             ㅁ내[아럼ㄴ엘ㄴㅁ얾ㄴ애ㅑ럼ㄴ애ㅣ랴ㅓㅁㄴ이[ㅐㅎㅁㄴㅇ러ㅔㅎㄴㅁ엃ㅁ내ㅔ럼ㄴ애ㅔ럼ㄴㅇ래ㅔㅓㅁㄴㅇ]] ㅁ내[아럼ㄴ엘ㄴㅁ얾ㄴ애ㅑ럼ㄴ애ㅣ랴ㅓㅁㄴ이[ㅐㅎㅁㄴㅇ러ㅔㅎㄴㅁ엃ㅁ내ㅔ럼ㄴ애ㅔ럼ㄴㅇ래ㅔㅓㅁㄴㅇ]]
             <img alt=""src="/img/cat05.jpeg">
         </div>
         <div id="content">
            <h1>#content 태그</h1>
         </div>
      </div>
      <!-- copyright / 회사 정보 내용 -->
      <div id="footer">
         <h1>#footer 태그</h1>
      </div>
   </div>
   </body>
</html>
```

**Result**
![layout-result](/assets/images/layout-result.png)