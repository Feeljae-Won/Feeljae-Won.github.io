---
title: "[DB] (서브쿼리) - 데이터 늘리기 , COUNT, 데이터 여러개 조회(IN)"
date: 2024-04-29 20:10:00 +0900
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### 데이터 늘리기
- 여러개의 데이터를 한꺼번에 등록시킨다. values를 사용하지 않는다.
- select문을 이용해서 데이터를 꺼내와서 다시 넣는다. x 2 씩 증가. 데이터가 한개라도 있어야 한다.
- 쿼리 안에 select 쿼리가 존재한다. - 서브 쿼리라고 한다.
- 괄호 안에 있는 내용 먼저 실행한다.
- insert문에 데이터 자리수와 ( ) 안에 조회하는 데이터 칼럼의 자리수가 동일해야 한다.
- values 는 한줄에 해당하는 데이터
```sql
-- 데이터를 늘리는 쿼리
INSERT INTO BOARD (NO, TITLE, CONTENT, WRITER, PW)
(SELECT BOARD_SEQ.NEXTVAL, TITLE, CONTENT, WRITER, PW FROM BOARD);
```

### COUNT
```sql
-- 전체 데이터의 개수를 가져오는 쿼리 - COUNT()
SELECT COUNT(NO) CNT FROM BOARD;
```

### 데이터 여러개 조회 (IN)
- 조건에서 `OR` 연산자를 이용하여 한 개의 항목에서 여러개의 데이터 검색을 할 때 `OR` 연산자를 사용
  - `IN` 연산자 대신 사용 가능
- UPDATE, DELETE 에서도 사용 가능

```sql
-- 번호 : 40, 45, 50 데이터 조회
SELECT * FROM BOARD WHERE NO = 40 OR NO= 45 OR NO =50 ORDER BY NO DESC;
SELECT * FROM BOARD WHERE NO IN (40, 45, 50) ORDER BY NO DESC;
```