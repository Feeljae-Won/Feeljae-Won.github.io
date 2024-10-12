---
title: "[DB] Group By 절"
categories:
  - docs
  - db
  - oracle
tags:
  - db
  - oracle
layout: single
---

### Group By 절
- **설명**: GROUP BY 절은 지정된 열의 값이 같은 행들을 그룹화하여 집계 함수(SUM, AVG, MAX, MIN, COUNT 등)를 적용할 수 있게 한다.
- **특징**: GROUP BY 절을 사용하면 데이터를 특정 기준으로 묶어 요약된 정보를 얻을 수 있다.

### 예시
- **기본 예시**: 각 부서별로 직원 수를 구한다.
  - **쿼리**:
    ```sql
    SELECT department_id, COUNT(*)
    FROM employees
    GROUP BY department_id;
    ```
  - **결과**: 각 부서의 직원 수가 반환된다.

- **SUM 함수와 함께 사용**: 각 부서별 총 급여를 구한다.
  - **쿼리**:
    ```sql
    SELECT department_id, SUM(salary)
    FROM employees
    GROUP BY department_id;
    ```
  - **결과**: 각 부서의 총 급여가 반환된다.

- **HAVING 절과 함께 사용**: 직원 수가 10명 이상인 부서만 선택한다.
  - **쿼리**:
    ```sql
    SELECT department_id, COUNT(*)
    FROM employees
    GROUP BY department_id
    HAVING COUNT(*) >= 10;
    ```
  - **결과**: 직원 수가 10명 이상인 부서의 정보가 반환된다.

## 여러 열로 그룹화
- **설명**: 여러 열을 기준으로 그룹화할 수 있다.
- **예시**: 부서와 직책별로 평균 급여를 구한다.
  - **쿼리**:
    ```sql
    SELECT department_id, job_id, AVG(salary)
    FROM employees
    GROUP BY department_id, job_id;
    ```
  - **결과**: 각 부서와 직책별 평균 급여가 반환된다.