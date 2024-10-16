---
title: "[Front-End] HTML 데이터 유효성 검사 "
date: 2024-05-31 19:40:00 +0900
categories:
  - docs
  - jsp
  - html
  - front-end
tags:
  - jsp
  - html
  - pattern
  - data Validation
  - front-end
layout: single
---

# 데이터 유효성 검사
- `HTML`에서 `form` 안에 `<input>` 태그에 있는 데이터가 적절한 유형의 데이터인지 또는 데이터가 비워져 있지 않은지에 대해 확인할 필요가 있다.
- `required` : 데이터 입력을 꼭 해야 하는 `<input>` 태그, 또는 `javascript`로도 처리할 수 있다.
- `pattern` : 입력한 데이터의 유형이 요구하는 형식과 일치 시키기 위해 사용한다.
  - **정규표현식** 참고 사이트 : ![https://regexr.com/](https://regexr.com)

## 예시
### ID 데이터 유효성 검사
```html
<!-- 데이터 유효성 검사 pattern : dkdlel - 3~20자, 맨 앞자 영문자, 뒤에는 영어 숫자
      유효성 검사에 위배되면 데이터 전달 안하고 메시지 출력
      - title 속성에 메시지를 사용. 없으면 기본 메시지 사용 -->
<td>
  <input type="text" id="id" name="id" required
      pattern="^[a-zA-Z][a-zA-z0-9]{2,19}$>"
      title="맨 앞자는 영문자, 뒤에는 영숫자, 3~20자 길이로 작성해야 합니다."
      placeholder="아이디 입력" maxlength="20" class="textInput">
</td>
```

### PW 데이터 유효성 검사
```html
<tr>
    <th>비밀번호</th>
    <!-- input 타입 : password - 비밀번호 입력, 입력한 텍스트가 표기 되지 않음. -->
    <!-- 데이터 유효성 검사 pattern : 비밀번호 -->
    <td>
        <input type="password" id="pw" name="pw" required
              pattern="^.{4.20}$>" title="비밀번호는 4~20자로 작성하셔야 합니다."
              placeholder="비밀번호 입력" maxlength="20" class="textInput">
    </td>
</tr>
<tr>
    <th>비밀번호 확인</th>
    <td>
        <input type="password" id="pw2" required
              pattern="^.{4.20}$>" title="비밀번호는 4~20자로 작성하셔야 합니다."
              placeholder="비밀번호 확인" maxlength="20" class="textInput">
    </td>
</tr>
```
![data-validation](/assets/images/data-validation.png)


### 이름 데이터 유효성 검사(한글)
```html
<tr>
    <th>이름</th>
    <td>
        <input type="text" id="name" name="name" required
              pattern="^[가-힣]{2,10}$" title="이름은 2~10자로 한글만 가능합니다."
              placeholder="한글 10자 이내" maxlength="10" class="textInput">
    </td>
</tr>
```
