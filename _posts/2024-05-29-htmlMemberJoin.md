---
title: "[Front-End] HTML 회원 가입 "
date: 2024-05-31 19:30:00 +0900
categories:
  - docs
  - jsp
  - html
  - front-end
tags:
  - jsp
  - html
  - member
  - front-end
layout: single
---

# HTML과 JSP의 차이
 - **HTML** : 정적 페이지 - 데이터 변경이 안됨
 - **JSP** : 동적 페이지 - 데이터 변경이 가능하고 DB와 연동이 가능함.

 ## 회원 가입 폼
 ```html
 <body>
    <form action="write.jsp">
      <!-- 아이디, 비밀번호, 비밀번호 확인, 이름, 성별, 생년월일, 연락처, 이메일, 
        우편번호, 기본 주소, 상세 주소, 사진, 관심 상품  -->
      <table>
        <tr>
          <!-- 열 병합 -->
          <th colspan="2">
            <h1>회원 가입</h1>
          </th>
        </tr>
        <!-- 테이블 행 -->
        <tr>
          <!-- 테이블 헤드 열1 -->
          <th>아이디</th>
          <!-- 테이블 데이터 열2 -->
          <!-- input tag의 기본 타입 : text : 글자 입력 - 생략 가능 -->
          <!-- id, class 속성 : 화면단에서 조작하기 위해서 지정 -->
          <!-- name 속성 : 서버에서 데이터를 받는 key에 해당. 사용자 입력이 value가 된다. -->
          <td><input type="text"id="id"name="id"required
                placeholder="아이디 입력"maxlength="20"class="textInput"></td>
        </tr>
        <tr>
          <th>비밀번호</th>
          <!-- input 타입 : password - 비밀번호 입력, 입력한 텍스트가 표기되지 않음. -->
          <td><input type="password"id="pw"name="pw"required
                placeholder="비밀번호 입력"maxlength="20"class="textInput"></td>
        </tr>
        <tr>
          <th>비밀번호 확인</th>
          <td><input type="password"id="pw2"required
                placeholder="비밀번호 확인"maxlength="20"class="textInput"></td>
        </tr>
        <tr>
          <th>이름</th>
          <td><input type="text"id="name"name="name"required
                placeholder="한글 10자 이내"maxlength="10"class="textInput"></td>
        </tr>
        <tr>
          <th>성별</th>
          <td>
            <!-- input tag 타입 : radio : 사용자가 한개만 선택할 수 있는 버튼
               넘겨 줄 값은 사용자가 입력하지 않고 value 속성으로 미리 저장해 놓는다.
               단, 한개만 선택할 수 있는 항목들의 name이 같아야 한다. --> 
            <!-- name 속성 : 서버에서 데이터를 받는 key에 해당.
               checked - radio, checkbox 입력을 체크되어 지도록 한다. --> 
                <input type="radio"name="gender"requiredvalue="남자"checked="checked">
            <b>남자 
                <input type="radio"name="gender"requiredvalue="여자">
            <b>여자 
          </td>
        </tr>
        <tr>
          <th>생년월일</th>
          <!-- input tag 타입 : date : 날짜 입력, 브라우저의 특성을 탄다.
             date 타입이 인식이 안되면 text로 진행된다. -->
          <td><input type="date"id="birth"name="birth"required
                class="textInput"></td>
        </tr>
        <tr>
          <th>연락처</th>
          <!-- input tag 타입 : tel : 전화 번호 입력, 브라우저의 특성을 탄다.
             date 타입이 인식이 안되면 text로 진행된다. -->
          <td>
            <div>
              <!-- 통신사 번호 : 010, 011, 017, 019 : 정해진 데이터 중 한개 선택 - select-->
              <!-- 서버에서 받는 데이터의 이름(KEY) name 인데 2개 이상 가능
                 서버에서 2개 이상 같은 name을 받을 때 배열로 받아서 처리 가능
                 multiple 속성으로 2개 이상 선택 가능 -->
              <select id="tel2"name="tel2">
                <!-- 선택항목 : option. 값은 속성 value 속성 지정
                        value가 없으면 option 태그 사이의 데이터가 값이 된다.
                        맨 처음 선택되어지게 하는 속성 : selected -->
                <option selected>010</option>
                <option>011</option>
                <option>017</option>
                <option value="019">019</option>
              </select>-
              <!-- JS로 숫자만 받게 하고 박스 크기 지정 -->
              <input type="text"size="4"maxlength="4"name="tel2">- 
                  <input type="text"size="4"maxlength="4"name="tel2">
            </div>
          </td>
        </tr>
        <tr>
          <th>이메일</th>
          <!-- input tag : email : email은 "@" 기호만 체크-->
          <td><input type="email"id="email"name="email"required
                placeholder="email"maxlength="10"class="textInput"></td>
        </tr>
        <tr>
          <th>우편번호</th>
          <!-- input tag : email : email은 "@" 기호만 체크-->
          <td><input type="text"id="postCode"name="postCode"required
                placeholder="우편번호"maxlength="10"class="textInput"></td>
        </tr>
        <tr>
          <th>기본 주소</th>
          <!-- input tag : email : email은 "@" 기호만 체크-->
          <td><input type="text"id="basicAddress"name="basicAddress"required
                placeholder="기본 주소 입력"maxlength="10"class="textInput"></td>
        </tr>
        <tr>
          <th>상세 주소</th>
          <!-- input tag : email : email은 "@" 기호만 체크-->
          <td><input type="email"id="detailAddress"name="detailAddress"required
                placeholder="상세 주소 입력"maxlength="10"class="textInput"></td>
        </tr>
        <tr>
          <th>사진</th>
          <!-- input tag : file -->
          <!-- name 속성 : 사용자 선택 파일이 value가 된다.
             form method 속성이 반드시 "post" 이어야만 한다.
             form 태그 속성에는 enctype="multipart/form-data"를 선언해야만 한다. -->
          <td><input type="file"id="photo"name="photo"
                class="textInput"></td>
        </tr>
        <tr>
          <th>관심 상품</th>
          <!-- input tag : checkbox : 여러개를 체크할 수 있다.-->
          <!-- name 속성 : name이 같으면 배열 값은 value 속성 이용 -->
          <td>
          <label>
            <input type="checkbox"id="interest"name="interest"
                value="아웃도어">아웃도어
          </label>
          <label>
            <input type="checkbox"id="interest"name="interest"
                value="악세서리">악세서리
          </label>
          <label>
            <input type="checkbox"id="interest"name="interest"
                value="신발">신발
          </label>
          <label>
            <input type="checkbox"id="interest"name="interest"
                value="잡화">잡화
          </label>
          <label>
            <input type="checkbox"id="interest"name="interest"
                value="전자제품">전자제품
          </label>
          </td>
        </tr>
        <tr>
          <td colspan="2">
            <button>가입</button>
          </td>
        </tr>
      </table>
    </form>
 </body>
 ```

 ## CSS
 ```css
 <styletype="text/css">
  table {
    /* 가운데 정렬 : 밖의 여백 */
    margin: 0 auto;
    width: 800px;
  }

  th, td {
    border: 1px hidden #000;
    padding: 5px;
  }

  th {
    width: 20%;
    background: #3366cc;
    color: white;
    background: #3366cc;
  }

  td {
    background: #99b3e6;
    color: white;
  }

  input, select, textarea {
    padding: 5px;
  }

  .textInput {
    /* 	width: 98%; */
    
  }
  #basicAddress, #detailAddress{
    width: 98%;
  }
  #email{
    width: 300px;
  }
  td > label {
    cursor: pointer;
  }
 </style>
 ```