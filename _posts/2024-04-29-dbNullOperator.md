---
title: "[DB] Null 연산"
date: 2024-04-29 19:50:00 +0900
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### NULL 연산

#### NULL 값
- **설명**: NULL 값은 아직 정의되지 않은 값이다. 0이나 공백과는 다르다.
- **특징**: NULL 값을 포함하는 연산의 결과는 항상 NULL이 된다.

#### 더하기 (+)
- **설명**: NULL 값과 숫자를 더하면 결과는 NULL이 된다.
- **예시**: `SELECT NULL + 2;` 결과는 `NULL`이 된다.

#### 빼기 (-)
- **설명**: NULL 값과 숫자를 빼면 결과는 NULL이 된다.
- **예시**: `SELECT NULL - 2;` 결과는 `NULL`이 된다.

#### 곱하기 (*)
- **설명**: NULL 값과 숫자를 곱하면 결과는 NULL이 된다.
- **예시**: `SELECT NULL * 2;` 결과는 `NULL`이 된다.

#### 나누기 (/)
- **설명**: NULL 값과 숫자를 나누면 결과는 NULL이 된다.
- **예시**: `SELECT NULL / 2;` 결과는 `NULL`이 된다.

#### NULL 처리 함수
- **NVL/ISNULL**: NULL 값을 다른 값으로 대체한다.
  - **예시**: `SELECT NVL(NULL, 0);` 결과는 `0`이 된다.
- **COALESCE**: 여러 표현식 중 첫 번째 NULL이 아닌 값을 반환한다.
  - **예시**: `SELECT COALESCE(NULL, 1, 2);` 결과는 `1`이 된다.

```sql
-- WHERE & NULL 예시
SELECT * FROM BOARD WHERE WRITER = NULL; -- 사용 가능
SELECT * FROM BOARD WHERE WRITER != NULL; -- 오류는 안나지만 NOT NULL은 연산이 안됨
SELECT * FROM BOARD WHERE WRITER IS NOT NULL; -- NOT NULL은 IS NOT NULL 사
```

#### NULL 관련 함수
```sql
-- NULL 인 경우는 0으로 처리해라 -> NVL()
SELECT NVL(NULL, 0) + 1 FROM DUAL;
```