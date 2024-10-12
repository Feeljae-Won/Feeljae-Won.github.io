---
title: "[DB] Index와 View"
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### VIEW
- VIEW를 생성하는 이유
  - 쿼리가 길고 복잡할 때
  - 사용 제한을 주고자 할 때

```SQL
-- VIEW TABLE을 이용한 처리를 위한 VIEW 생성
-- VIEW = 가상 테이블
CREATE OF REPLACE VIEW NOTICE_PRE
AS
SELECT NO, TITLE, CONTENT, STARTDATE, ENDDATE, UPDATEDATE WRITEDATE
FROM NOTICE
-- 시작일이 현재보다 작고 종료일이 현재보다 크다. - 현재가 시작일과 종료일 사이에 있어야 한다.
WHERE SYSDATE >= STARTDATE AND TRUNC(SYSDATE) <= ENDDATE
ORDER BY UPDATEDATE DESC, NO DESC;
```
- 아래와 같이 VIEW 테이블로 조회할 수 있다.
```SQL
SELECT NO. TITLE, CONTENT, STARTDATE, ENDDATE, WRITEDATE
FROM NOTICE_PRE;
```

### INDEX
- WHERE 절에 의해 데이터 분포가 테이블 전체의 약 10 ~ 15%일 경우 생성한다.
- 검색을 자주하는 칼럼
- 한 테이블에 3 ~ 4개 정도 생성

- **INDEX 만들지 말아야 하는 경우**
  - 전체 데이터의 80% 이상 INDEX를 사용하는 경우
  - 자주 데이터가 수정 되는 경우

```SQL
-- INDEX - 속도 빠르게
CREATE INDEX BOARD_NO_IDX
ON BOARD(NO DESC);

CREATE INDEX MEMBER_NM_IDX
ON MEMBER(NAME);

CREATE INDEX BOARD_MEMBER_BD_IDX
ON MEMBER(NAME, BIRTH);
```