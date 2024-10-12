---
title: "[DB] 연결 연산자"
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### 연결 연산자 (||)
- **설명**: 두 개 이상의 문자열을 연결하여 하나의 문자열로 만든다.
- **예시**: `SELECT 'Hello' || ' ' || 'World';` 결과는 `Hello World`가 된다.

### 열 연결
- **설명**: 두 개 이상의 열 값을 연결하여 하나의 문자열로 만든다.
- **예시**: `SELECT first_name || ' ' || last_name FROM employees;` 결과는 `John Doe`와 같이 된다.

### 문자열과 열 연결
- **설명**: 문자열과 열 값을 연결하여 하나의 문자열로 만든다.
- **예시**: `SELECT 'Employee: ' || first_name || ' ' || last_name FROM employees;` 결과는 `Employee: John Doe`가 된다.

### 공백 추가
- **설명**: 문자열 사이에 공백을 추가하여 연결한다.
- **예시**: `SELECT first_name || ' ' || last_name FROM employees;` 결과는 `John Doe`가 된다.

### 숫자와 문자열 연결
- **설명**: 숫자와 문자열을 연결하여 하나의 문자열로 만든다.
- **예시**: `SELECT 'Salary: ' || salary FROM employees;` 결과는 `Salary: 5000`과 같이 된다.

#### 예시
```sql
SELECT (NO || '-' || TITLE) DATA FROM BOARD ORDER BY NO DESC;
```
|DATA| | |
|---|---|---|
|1-JAVA| | |
|2-ORACLE| | |