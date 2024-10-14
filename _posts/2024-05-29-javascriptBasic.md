---
title: "[Front-End] Javascript 기본, 용어정리"
date: 2024-05-29 19:20:00 +0900
categories:
  - docs
  - javascript
  - front-end
tags:
  - javascript
  - front-end
layout: single
---

# JavaScript에 대한 설명

JavaScript는 웹 페이지에 동적인 기능을 추가하기 위해 사용되는 프로그래밍 언어이다. HTML과 CSS가 각각 웹 페이지의 구조와 디자인을 담당한다면, JavaScript는 웹 페이지에 인터랙티브한 요소와 동작을 부여하는 역할을 한다. 또한, JavaScript는 클라이언트 측에서 실행되는 언어이지만, Node.js와 같은 환경을 통해 서버 측에서도 사용할 수 있다.

## JavaScript의 주요 특징

1. **동적 프로그래밍 언어**
   - JavaScript는 동적이며, 실행 시점에 변수의 타입이 결정되고 변경될 수 있다. 다른 언어와 달리 변수를 선언할 때 명시적인 타입 지정이 필요하지 않다.

2. **클라이언트 측 스크립트**
   - JavaScript는 웹 브라우저에서 실행되며, 사용자가 웹 페이지와 상호작용할 수 있게 해준다. 예를 들어, 버튼 클릭, 입력 폼 제출, 마우스 이벤트 등의 상호작용을 처리할 수 있다.

3. **비동기 처리**
   - JavaScript는 **비동기 프로그래밍**을 지원하며, 이를 통해 페이지 로딩 중에도 다른 작업을 동시에 수행할 수 있다. 대표적으로 **콜백 함수**, **프로미스(Promise)**, 그리고 **async/await**를 사용해 비동기 처리를 구현할 수 있다.

4. **다중 플랫폼 지원**
   - JavaScript는 웹 브라우저 외에도 Node.js 환경에서 서버 측에서 사용될 수 있으며, 모바일 애플리케이션 개발, 데스크톱 애플리케이션 개발 등 여러 플랫폼에서 활용된다.

## JavaScript의 기본 문법

1. **변수 선언**
   - JavaScript에서는 `var`, `let`, `const`를 사용해 변수를 선언할 수 있다.
   - `let`과 `const`는 블록 범위(block scope)를 가지며, `const`는 값이 변경되지 않는 상수를 선언할 때 사용한다.

   ```javascript
   let name = "John";
   const age = 30;
   var city = "New York";
   ```

2. **함수**
   - JavaScript에서는 함수를 정의하고 호출할 수 있으며, 함수는 `function` 키워드 또는 화살표 함수(ES6)를 사용해 작성할 수 있다.

   ```javascript
   // 함수 선언
   function greet(name) {
       return `Hello, ${name}!`;
   }

   // 함수 호출
   greet("Alice");

   // 화살표 함수
   const add = (a, b) => a + b;
   ```

3. **조건문과 반복문**
   - JavaScript는 `if`, `else if`, `else`를 사용한 조건문과 `for`, `while` 같은 반복문을 제공한다.

   ```javascript
   let number = 10;

   if (number > 0) {
       console.log("양수입니다.");
   } else if (number < 0) {
       console.log("음수입니다.");
   } else {
       console.log("0입니다.");
   }

   for (let i = 0; i < 5; i++) {
       console.log(i);
   }
   ```

4. **객체와 배열**
   - JavaScript에서는 객체와 배열을 사용해 데이터를 구조화할 수 있다.

   ```javascript
   // 객체
   const person = {
       name: "John",
       age: 30,
       city: "New York"
   };

   // 배열
   const fruits = ["Apple", "Banana", "Orange"];
   ```

## JavaScript의 활용 사례

1. **DOM 조작**
   - JavaScript는 DOM(Document Object Model)을 통해 HTML 문서의 요소를 동적으로 조작할 수 있다. 예를 들어, 특정 요소를 선택하고 그 속성을 변경하거나, 새로운 요소를 추가할 수 있다.

   ```javascript
   const element = document.getElementById("myElement");
   element.textContent = "Hello, World!";
   ```

2. **이벤트 처리**
   - JavaScript를 사용해 사용자 상호작용에 대한 이벤트를 처리할 수 있다. 예를 들어, 버튼을 클릭할 때 특정 동작을 수행할 수 있다.

   ```javascript
   const button = document.querySelector("button");
   button.addEventListener("click", () => {
       alert("버튼이 클릭되었습니다.");
   });
   ```

3. **비동기 요청(AJAX)**
   - JavaScript는 서버와 비동기 통신을 할 수 있으며, 이를 통해 페이지를 다시 로드하지 않고도 데이터를 주고받을 수 있다. 예를 들어, `fetch` API를 사용해 서버에 데이터를 요청할 수 있다.

   ```javascript
   fetch("https://api.example.com/data")
       .then(response => response.json())
       .then(data => console.log(data))
       .catch(error => console.error("Error:", error));
   ```

4. **프론트엔드 프레임워크**
   - JavaScript는 React, Vue.js, Angular와 같은 프론트엔드 프레임워크에서 사용되며, 대규모 웹 애플리케이션을 효과적으로 관리할 수 있게 해준다.

## JavaScript의 장점

1. **다양한 용도**
   - JavaScript는 웹 개발 외에도 서버 개발, 모바일 애플리케이션, 데스크톱 애플리케이션 등 다양한 환경에서 사용될 수 있다.

2. **풍부한 생태계**
   - JavaScript는 풍부한 라이브러리와 프레임워크를 제공하며, 개발자들이 다양한 도구를 활용할 수 있다. 또한, 커뮤니티가 크고 활발하게 발전하고 있다.

3. **빠른 학습 곡선**
   - JavaScript는 상대적으로 배우기 쉬운 언어로, 초보자도 빠르게 웹 페이지의 동작을 구현할 수 있다.

JavaScript는 웹 페이지에 필수적인 프로그래밍 언어로, 동적이고 인터랙티브한 기능을 구현하는 데 필수적인 도구이다.
