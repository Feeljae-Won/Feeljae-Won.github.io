---
title: "[DB] 단일 행 함수"
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

## 단일 행 함수

### 문자형 함수
```sql
-- 문자형 함수
SELECT UPPER(TITLE) FROM BOARD; -- UPPER(~) 대문자로 변환
SELECT LOWER('TEST') FROM DUAL; -- LOWER(~) 소문자로 변환

-- 문자열
SELECT TITLE, LENGTH(TITLE) FROM BOARD WHERE NO < 30; -- LENGTH(~) 글자 개수(한글 1글자 당 1개)
SELECT DISTINCT WRITER FROM BOARD; -- DISTINCT 중복된 것을 제외한 데이터

-- 작성자의 문자 길이를 알아낼 때 1) LENGTH(WRITER)  2) LENGTHB(WRITER)
SELECT NO, TITLE, CONTENT, WRITER, LENGTH(WRITER) LENGTH, LENGTHB(WRITER) LENGTHB
FROM BOARD
WHERE NO = 21; -- LENGTH(~) 글자 BYTE 수 (한글 3BYTE/자)

-- 공백 제거
SELECT '[' || '               JAVA          ' || ']' FROM DUAL;
SELECT '[' || TRIM('               JAVA          ') || ']' FROM DUAL; -- TRIM('문자열') 단어 앞 뒤의 공백 제거
SELECT '[' || LTRIM('               JAVA          ') || ']' FROM DUAL; -- LTRIM('문자열') 왼쪽의 공백 제거
SELECT '[' || RTRIM('               JAVA          ') || ']' FROM DUAL; -- RTRIM('문자열') 오른쪽의 공백 제거
```

### 숫자형 함수
```SQL
-- 숫자형 함수

-- 실수형 처리
-- ROUND(실수, 자리수) -> 소수점 기준 - 소수점 이하 자리 수 까지 표시 - 반올림
SELECT 1234.567 NUM, ROUND(1234.567, 2) ROUND FROM DUAL;

-- TRUNC(실수, 자리수) -> 소수점 기준 -소수점 자리 수 이하 버림 - 내림
-- FLOOR(실수) -> 소수점 기준 실수 값을 넘지 않는 정수 최대 값 = 소수점 제거 : TRUNC
-- CEIL(실수) -> 올림
SELECT 1234.567 NUM, ROUND(1234.567, 2) ROUND, TRUNC(1234.567, 2) TRUNC, -- 소수
  FLOOR(1234.567 * 100) FLOOR, CEIL(1234.567) CEIL -- 정수
FROM DUAL;
```
|NUM|ROUND|TRUNC|FLOOR|CEIL|
|---|---|---|---|---|
|1234.567|1234.57|1234.56|123456|1235|

### 데이터 형 변환
```SQL
--- 데이터 형 변환

-- TO_CHAR : 문자열로 변환. 날짜형 -> 문자열,  숫자형 -> 문자열
--         : 사용자가 보기 편한 형태로 변환 하기 위함

-- 날짜 -> 문자열로 : 날짜 계산이 안된다.
SELECT SYSDATE FROM DUAL; -- 24/04/29
SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD') TODAY FROM DUAL; -- 2024-04-29
SELECT CURRENT_TIMESTAMP FROM DUAL; -- 24/04/29 16:37"12.286000000 ASIA/SEOUL
SELECT TO_CHAR(CURRENT_TIMESTAMP, 'YYYY' || '년' || 'MM' || '월' || 'DD' || '일') FROM DUAL;
SELECT
  TO_CHAR(CURRENT_TIMESTAMP, 'YYYY') || '년'
  || TO_CHAR(CURRENT_TIMESTAMP, 'MM') || '월'
  || TO_CHAR(CURRENT_TIMESTAMP, 'DD') || '일'
  TODAY 
FROM DUAL; -- 2024년 04월 29일

-- 숫자 -> 문자열로 변환
SELECT '[' || TO_CHAR(1234.1234, 's999,999.99999') || ']' FROM DUAL; -- [ +1,234.12340 ] // s -> sign
SELECT '[' || TO_CHAR(1234.1234, 's0999,999.99999') || ']' FROM DUAL; -- [ +0001,234.12340 ] // 빈 공간을 0으로 채워라
```