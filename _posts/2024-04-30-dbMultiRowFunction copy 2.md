---
title: "[DB] 다중 행 함수"
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### 단일 행 함수

#### SUM 함수
- **설명**: 지정한 열의 값을 모두 더한다.
- **예시**: `SELECT SUM(salary) FROM employees;` 결과는 모든 직원의 급여 합계가 된다.

#### COUNT 함수
- **설명**: 지정한 열의 값을 개수로 센다.
- **예시**: `SELECT COUNT(*) FROM employees;` 결과는 직원 수가 된다.

#### MAX 함수
- **설명**: 지정한 열의 최대값을 반환한다.
- **예시**: `SELECT MAX(salary) FROM employees;` 결과는 가장 높은 급여가 된다.

#### MIN 함수
- **설명**: 지정한 열의 최소값을 반환한다.
- **예시**: `SELECT MIN(salary) FROM employees;` 결과는 가장 낮은 급여가 된다.

#### AVG 함수
- **설명**: 지정한 열의 평균값을 반환한다.
- **예시**: `SELECT AVG(salary) FROM employees;` 결과는 평균 급여가 된다.