---
title: "[DB] LIKE 연산자"
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### LIKE 연산자
- 문자열이 포함되어 있는 데이터 찾기의 `LIKE` 연산자 - `%`와 함께 사용한다. - `&`는 모든 글자를 대신한다.
- `LIKE` 연산자라도 `%`가 없으면 `=`과 같다.
- 게시판 종류의 검색에 주료 사용 -- 쇼핑몰 종류는 = 비교를 자주 사용.
```sql
-- LIKE 연산자
SELECT * FROM BOARD WHERE TITLE = 'ORACLE'; -- 정확히 같아야 조회
-- 포함되어 있으면 조회, %는 붙히는 쪽으로 어떠한 데이터가 와도 상관 없다.
SELECT * FROM BOARD WHERE TITLE LIKE '%O%';
-- 2개 이상 조건을 사용할 때는 OR 사용
SELECT * FROM BOARD WHERE TITLE LIKE '%O%' OR CONTENT LIKE '%D%' OR WRITER LIKE '%F%';
```