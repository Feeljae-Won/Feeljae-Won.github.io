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
   - `<b>` : 글자를 두껍게 만드는 태그 == `<strong>`
   - `<i>` : 기울어진 글자
   - `<small>` : 작은 글자
   - `<sub>` : 아래 첨자
   - `<sup>` : 위 첨자
   - `<ins>` : 밑줄 글자
   - `<del>` : 취소선이 그어진 글자

   **특수문자 표기**
   - `&lt;`p`&lt` : `<p>` - 꺽쇄를 사용하고 싶을 땐 특수 문자를 사용해야 한다.
   - `&amp;`lt; - [`&lt;`],                   `&amp;`gt; - [`&gt;`]
      - 결과 : `&lt; - [<], &gt; - [>]`
      - 공백은 한개만 인정된다.
   - `&amp;`nbsp; - [`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`]
      - 결과 : `&nbsp; - [     ]`
      - nbsp : 공백 문자

   ```html
   <h1>제목 1</h1>
   <p>이것은 단락입니다.</p>
   <strong>중요한 텍스트</strong>와 <em>강조된 텍스트</em>입니다.
   ```

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

   **Input Type**
   - `text`
      - 기본. 생략 가능
   - `password`
      - 비밀번호 입력, 입력한 텍스트가 표기되지 않음.
   - `radio`
      - 사용자가 한개만 선택할수 있는 버튼
      - 넘겨 줄 값은 사용자가 입력하지 않고 value 속성으로 미리 저장해 놓는다.
      - 단, 한개만 선택할 수 있는 항목들의 name이 같아야 한단.
      - `checked` : 처음에 체크되어 지도록 한다.
   - `date`
      - 날짜 입력, 브라우저의 특성을 탄다.
      - `date` 타입이 인식이 안되면 `text`로 진행된다.
   - `tel`
      - 전화 번호 입력, 브라우저의 특성을 탄다.
   - `number`
      - 숫자만 입력
      - `min` : 최소 값
      - `max` : 최대 값
   - `email`
      - `@` 기호만 체크
   - `file`
      - 사용자가 선택한 파일이 value가 된다. (`name` 속성)
      - `form method` 속성이 반드시 `post` 방식 이어야만 한다.
      - `form` 태그 속성에는 `enctye="multipart/form-data`를 선언해야만 한다. 
   - `checkbox`
      - 여러개를 체크할 수 잇다.
      - `name`이 같으면 배열 값은 value 속성 이용 (`name` 속성)
   - `select ~ option`
      - `select` : 정해진 데이터 중 한개 선택
      - `option` : 선택 항목 - 값은 속성 value 속성 지정, value가 없으면 `option` 태그 사이의 값이 된다.
      - `selected` : 맨 처음 선택 되어지게 하는 속성
      - `multiple` : 여러 개 선택할 수 있다.


	```html
   <body>
      <!-- 사용자에게 데이터 입력하는 태그 -->
      <!-- 데이터를 넘기는 방법을 생략하면 get 방식 -->
      <form action="write.jsp"method="post">
         <!-- 데이터 한줄로 입력 : input. 
      id, class : 모든 태그에 붙일 수 있다. 쉽게 선택(css나 JS에서) 
      name : 데이터를 넘길 때 사용되는 key. key=value key-title, value - 입력 값 
      maxlength : 입력할 수 있는 최대 글자 수.
      type : 기본 타입은 text이고 생략 가능함. 
      required : 필수 입력 항목
      placeholder : 데이터가 입력이 되지 않았을 때 나타나는 문구
      readonly : 수정 불가 -->
         제목 <input id="title"name="title"maxlength="10"required
               placeholder="제목 입력. 10자 이내 작성"> <br>
         내용 <textarea rows="7"cols="100"id="content"name="content"placeholder="내용을 입력해 주세요. 700자 이내.">
            </textarea> <p>
         작성자 <input id="writer"name="writer"maxlength="10"required
               placeholder="작성자 입력"> <br>
         비밀번호 <input id="pw"name="pw"maxlength="20"requiredtype="password"
               placeholder="비밀번호 입력"> <br>
         비밀번호 <input id="pw2"name="pw2"maxlength="20"requiredtype="password"
               placeholder="비밀번호 확인 입력"> <br>
         <!-- button의 기본 타입 : submit : click:submit()를 호출해서 데이터를 넘기는 처리 한다. 
                     reset : 페이지의 처음 데이터로 세팅해 준다. 
                     button : 버튼 처럼 보이고 동작은 안한다. 동작은 JS를 이용하여 처리 -->
         <button type="submit">등록</button>
         <button type="reset">다시 입력</button>
         <button type="button">취소</button>
      </form>
   </body>
	```
