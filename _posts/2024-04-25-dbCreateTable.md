---
title: "[DB] 테이블 생성"
date: 2024-04-25 19:00:00 +0900
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---
### 참조키가 지워질 때 같이 삭제하기 - ON DELETE CASCADE
- `ON DELETE CASCADE` : 위에서 부터 아래까지 전부 지운다.
```SQL
CREATE TABLE MEMBER (
  .
  .
  GRADENO NUMBER(2) DEFAULT 1 REFERENCES GRADE(GRADENO) ON DELETE CASCADE
);
```

### 참조키가 지워질 때 지워지지 않고 NULL로 저장 - ON DELETE SET NULL
```SQL
CREATE TABLE MEMBER (
  .
  .
  GRADENO NUMBER(2) DEFAULT 1 REFERENCES GRADE(GRADENO) ON DELETE SET NULL
);
```

### 테이블 생성 - 일반 게시판 스키마

1. 객체 삭제
2. 객체 생성(명세서에 맞게 테이블 생성)
3. 샘플데이터 넣기

![DBTableDoc](/assets/images/BoardDBTableDoc.png)

```sql
-- 일반 게시판 테이블 스키마

-- 1. 객체 제거
-- CASCADE -> 다음 단계로 떨어진다. - 지우려는 것과 연결되어 있는 것을 지우자. (=> CONSTRAINTS)
-- CONSTRAINTS -> 제약 조건
-- PURGE -> 지우면 휴지통에 담기게 된다. 휴지통에 안 담고 지우자
DROP TABLE board CASCADE CONSTRAINTS PURGE;
DROP SEQUENCE board_seq; -- DROP 하게 되면 기본 값은 1

-- 2. 객체 생성
CREATE TABEL board (
	no NUMBER PRIMARY KEY, -- null이 아니고 중복이 되지 않는 항목(칼럼)
	title VARCHAR2(300) NOT NULL, -- 한글은 3byte, 300 = 한글 100자 / NOT NULL -> 비워져 있으면 안된다.
	content VARCHAR2(2000) NOT NULL, -- 2000byte
	writer VARCHAR2(30) NOT NULL, -- 30byte, 한글 10자
	writeDate DATE DEFAULT sysdate, -- DEFAULT = 등록할 필요가 없다.
	hit NUMBER DEFAULT 0, -- 길이 지정 안하면 LONG 타입
	pw VARCHAR2(20) NOT NULL -- 20byte, 패스워드 20자 까지
);

CREATE SEQUENCE board_seq;

-- 3. 샘플 데이터 넣기
INESRT INTO board(no, title, content, writer, pw)
VALUES(board_seq.nextval, 'java', 'program', 'won', '1111');
INSERT INTO board(no, title, content, writer, pw)
VALUES(board_seq.nextval, 'oracle', 'DB', 'Feel', '1111');

-- 4. 조회하기
SELECT * FROM board;
```

### 테이블 생성 - 회원관리 테이블
![memberTable](/assets/images/memberTable.png)
```sql
-- 회원등급 & 회원 테이블

-- 1. 객체 제거
-- FK 테이블을 먼저 지우고 PK는 나중에 지운다.
DROP TABLE member CASCADE CONSTRAINTS PURGE;
DROP TABLE grade CASCADE CONSTRAINTS purge;

-- 2. 객체 생성
-- PK 테이블을 먼저 만들고 FK 테이블을 나중에 만든다.
CREATE TABLE grade (
    gradeNo number(2) PRIMARY KEY,
    gradeName VARCHAR2(20) not null
);

CREATE TABLE member (
    id VARCHAR2(40) PRIMARY key,
    pw VARCHAR2(20) NOT NULL,
    name VARCHAR2(30) NOT NULL,
    gender VARCHAR2(6) NOT NULL check(gender in('남자','여자')), -- (gender = '남자' or gender = '여자')
    birth date NOT NULL,
    email varchar2(30) not null,
    tel VARCHAR2(13),
    regDate date DEFAULT sysdate,
    conDate date DEFAULT sysdate,
    status VARCHAR2(6) DEFAULT '정상' check(status in('정상','제재','탈퇴','휴면')),
    photo VARCHAR2(200),
    newMsgCnt NUMBER DEFAULT 0,
    -- REFERENCES -> foreign key
    gradeNo NUMBER(2) DEFAULT 1 REFERENCES grade(gradeNo) 
    -- ON DELETE CASCADE
    -- ON DELETE SET NULL
);
create SEQUENCE memberNo_seq;

-- 3. 샘플 데이터
-- 1) PK 데이터를 먼저 넣는다. - grade
insert into grade -- 테이블 이름만 쓰는 경우는 모든 컬럼에 대해서 순서대로 데이터를 입력할 때 생략 가능
values (1,'일반회원');
insert into grade -- 테이블 이름만 쓰는 경우는 모든 컬럼에 대해서 순서대로 데이터를 입력할 때 생략 가능
values (2,'쇼핑몰관리자');
insert into grade 
values (9,'관리자');
commit;

-- 2) FK 데이터를 PK 뒤에 넣는다. - member
-- 일반 회원 가입
-- 관리자 등록
insert into member(id, pw, name, gender, birth, tel, email, photo, gradeNo)
values ('admin','1111','관리자','남자','1992-08-11','010-2222-3333', 'test@test.com', '/update/member/admin.jpg', 9);
commit;
insert into member(id, pw, name, gender, birth, tel, email, photo)
values ('test','1111','테스트','남자','1999-01-01','010-1234-1234', 'shop@shop.com', '/update/member/test.jpg');
-- 쇼핑몰 관리자 가입
insert into member(id, pw, name, gender, birth, tel, email, photo, gradeNo)
values ('shop','1111','쇼핑몰 관리자','여자','1999-01-01','010-1234-1234', 'admin@admin.com', '/update/member/test.jpg', 2);


-- 4. 조회하기
select * from grade;
select * from member;
select m.email, m.pw, m.name, m.gender, m.birth, m.tel, m.regdate, m.condate, m.status, m.photo, g.gradeNo
from member m, grade g where m.gradeNo = g.gradeNo;
commit;
```

### 테이블 생성 - 공지사항 테이블
```sql
-- 게시판 스키마 작성

-- 삭제
DROP TABLE notice CASCADE CONSTRAINTS purge;
DROP SEQUENCE notice_seq;

-- 테이블 생성

CREATE TABLE notice (
    no number PRIMARY KEY,
    title VARCHAR2(300) NOT NULL,
    content VARCHAR2(2000) NOT NULL,
    startDate date DEFAULT sysdate,
    endDate date DEFAULT '9999-12-30',
    writeDate date DEFAULT sysdate,
    updateDate date DEFAULT sysdate
);

CREATE SEQUENCE notice_seq;


-- 샘플 데이터
insert into notice (no, title, content)
VALUES (notice_seq.nextval,'공지사항 샘플', '공지사항 샘플입니다.');
commit;

-- 데이터 조회
select * from notice;
```