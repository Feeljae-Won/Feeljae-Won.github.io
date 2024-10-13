---
title: "[DB] Between - and 연산자, 숫자 잘라내기
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### Between - And 연산자
- 번호가 10보다 크거나 같고 35보다 작은 범위의 데이터 조회 - `AND` 연산자
- 숫자나 날짜 범위인 경우 `BETWEEN` 연산자 사용 가능
```sql
-- 번호가 10보다 크거나 같고 35보다 작거나 같은 범위의 데이터 조회. - AND 연산자
SELECT * FROM BOARD WHERE NO >= 10 AND NO <= 35 ORDER BY NO DESC;

-- 숫자 범위인 경우 BETWEEN 연산자 사용 가능
SELECT * FROM BOARD WHERE NO BETWEEN 10 AND 35 ORDER BY NO DESC;
```

### 숫자 잘라내기 (TRUNC())
- `DATE` 형식을 날짜 비교할 경우 뒤에 시간을 지우고 비교를 하기 위해 숫자를 잘라낸다.
```sql
-- TRUNC() : 숫자인 경우 소수점 이하 잘라내기, 날짜형인 경우는 시간 정보 잘라내기
SELECT NO, TITLE, CONTENT, WRITER, TO_CHAR(WRITEDATE, 'YYYY-MM-DD') WRITEDATE, HIT
FROM BOARD
WHERE TRUNC(WRITEDATE) - '2024-04-26';
```

### BETWEEN - AND 연산자로 페이지 처리 예시
```sql
--- 페이지 처리

-- 모든 데이터를 가져오자.
SELECT NO, TITLE, WRITER, WRITEDATE, HIT FROM BOARD
ORDER BY NO DESC;

-- 데이터가 많은 경우 사용자가 데이터를 보기가 불편하다. 그래서 페이지 처리를 한다.
-- 1. 페이지 : 10개의 데이터 - 전체 데이터 앞에 순서 번호를 붙혀서 1 ~ 10 가져오기
--  1) 원본 데이터 가져오기
SELECT NO, TITLE, WRITER, WRITEDATE, HIT FROM BOARD
ORDER BY NO DESC;

--  2) 순서 번호 붙히기 - ROWNUM 칼럼 앞에 추가 : 중간에 삭제되는 데이터의 빈 공간을 채우기 위해
SELECT ROWNUM RNUM, NO, TITLE, WRITER, WRITEDATE, HIT
FROM (
  SELECT NO, TITLE, WRITER, WRITEDATE, HIT
  FROM BOARD
  ORDER BY NO DESC
)

--  3) 페이지 정보에 맞는 데이터 가져오기
SELECT NO, TITLE, WRITER, WRITEDATE, HIT
FROM (
  SELECT ROWNUM RNUM, NO, TITLE, WRITER, WRITEDATE, HIT
  FROM (
    SELECT NO, TITLE, WRITER, WRITEDATE, HIT
    FROM BOARD
    ORDER BY NO DESC
  )
)
WHERE RNUM BETWEEN 1 AND 10;
```
