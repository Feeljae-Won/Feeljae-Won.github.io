---
title: "[Front-End] HTML 기본, 용어정리"
date: 2024-05-29 19:00:00 +0900
categories:
  - docs
  - html
  - front-end
tags:
  - html
  - front-end
layout: single
---
# HTML에 대한 설명
- HTML(HyperText Markup Language)은 웹 페이지를 구성하는 데 사용되는 마크업 언어이다. 웹 브라우저가 문서를 렌더링하여 사용자에게 콘텐츠를 보여줄 수 있도록 문서의 구조와 내용을 정의하는 역할을 한다. HTML은 웹 페이지의 기본적인 요소들을 정의하며, 제목, 단락, 이미지, 링크, 리스트 등 다양한 콘텐츠를 표현할 수 있다.

## HTML의 주요 특징

1. **마크업 언어**
   - HTML은 프로그래밍 언어가 아닌 마크업 언어이다. 태그(tag)를 사용해 문서의 구조를 표현하며, 각 태그는 특정한 기능을 수행하거나 콘텐츠를 특정 형식으로 나타내기 위한 역할을 한다.

2. **태그와 요소**
   - HTML 문서는 여러 태그로 구성되며, 태그는 `<tagname>` 형식으로 작성된다. 시작 태그(`<tagname>`)와 종료 태그(`</tagname>`) 사이에 콘텐츠가 들어가며, 이 전체를 요소라고 부른다.
   - 예를 들어, `<p>Hello, World!</p>`는 단락(paragraph)을 나타내는 HTML 요소로, "Hello, World!" 텍스트를 단락 형태로 표현한다.

3. **속성(Attribute)**
   - HTML 태그는 속성을 가질 수 있으며, 속성은 태그에 추가 정보를 제공한다. 속성은 `name="value"` 형태로 작성하며, 시작 태그 안에 위치한다.
   - 예를 들어, `<a href="https://www.example.com">Visit Example</a>`에서 `href` 속성은 링크의 목적지를 지정한다.

4. **HTML 문서의 구조**
   - HTML 문서는 기본적으로 다음과 같은 구조를 따른다:
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <meta charset="UTF-8">
         <title>문서 제목</title>
     </head>
     <body>
         <h1>헤더 1</h1>
         <p>여기에 단락이 들어갑니다.</p>
     </body>
     </html>
     ```
   - `<!DOCTYPE html>`는 HTML5 문서를 선언하며, `<html>` 요소는 전체 HTML 문서를 감싸는 루트 요소이다.
   - `<head>` 요소에는 문서의 메타데이터(문자 인코딩, 제목, 스타일 시트 등)가 포함되며, `<body>` 요소에는 실제로 사용자에게 표시되는 콘텐츠가 포함된다.

## 주요 HTML 태그와 예제

1. **텍스트 관련 태그**
   - `<h1> ~ <h6>`: 제목을 나타내며, 숫자가 작을수록 더 큰 글씨로 표시된다.
   - `<p>`: 단락을 나타낸다.
   - `<strong>`: 굵은 글씨를 나타낸다.
   - `<em>`: 기울임꼴을 나타낸다.

   ```html
   <h1>제목 1</h1>
   <p>이것은 단락입니다.</p>
   <strong>중요한 텍스트</strong>와 <em>강조된 텍스트</em>입니다.

2. **링크와 이미지**
	- `<a>`: 하이퍼링크를 정의하며, `href` 속성으로 링크할 URL을 지정한다.
	- `<img>`: 이미지를 표시하며, `src` 속성으로 이미지 파일의 경로를 지정한다.
	```html
	<a href="https://www.example.com">Example 사이트 방문</a>
	<img src="image.jpg" alt="설명 텍스트">
	```

3. **리스트**
	- 순서가 있는 리스트(`<ol>`)와 순서가 없는 리스트 (`<ul>`)가 있으며, 각 항목은 `<li>` 태그로 감싼다.
	```html
	<ol>
		<li>첫 번째 항목</li>
		<li>두 번째 항목</li>
	</ol>

	<ul>
		<li>첫 번째 항목</li>
		<li>두 번째 항목</li>
	</ul>
	```

4. **폼 (Form)**
	- 사용자 입력을 받을 수 있는 양식을 정의하며, `<form>` 요소 안에 `<input>`, `<textarea>`, `<button>` 등을 포함한다.
	```html
	<form action="/submit" method="post">
		<label for="name">이름:</label>
		<input type="text" id="name" name="name">
		<button type="submit">제출</button>
	</form>
	```
