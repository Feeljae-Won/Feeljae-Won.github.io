---
title: "[Java] 예외처리 (try ~ catch)"
date: 2024-05-03 19:00:00 +0900
categories:
  - docs
  - java
tags:
  - java
layout: single
---

## 예외 처리
- **일반 예외** Exception
  - try ~ catch ~ finally
- **실행 예외** Runtime Exception

### 기본 예외 처리
```java
package ch11exception;

public class ExceptionExample {
  
  public static void main(String[] args) {
    
    // 1. 데이터 세팅
    // 2. 연산 /0
    // 3. 출력
    System.out.println("프로그램 시작");
    int a = 10;
    int result = 0;
    
    // 예외 처리
    try {
      // result = a/ 0; // 예외 발생
      result = a/ 3; // 예외 발생
      System.out.println("연산 완료");
    } catch(ArithmeticException e) {
      // e.printStackTrace(); // 개발자가 보기 위해 꼭 사용 해야 함. 개발자 코드
      System.out.println("연산 오류 발생 - 다시 한번 시도해 주세요.");
    } finally {
      System.out.println("반드시 실행되는 부분");
    }
    
    System.out.println(result);
    
    System.out.println("프로그램 끝");
    
  } // end of main ()
} // end of class
```

### Thorws
```java
package ch11exception;

public class ExceptionExample {
  
  public static void main(String[] args) {
    
    // 1. 데이터 세팅
    // 2. 연산 /0
    // 3. 출력
    System.out.println("프로그램 시작");
    int a = 10;
    int result = 0;
    
//		// 예외 처리
//		try {
//			// result = a/ 0; // 예외 발생
//			result = a/ 3; // 예외 발생
//			System.out.println("연산 완료");
//		} catch(ArithmeticException e) {
//			// e.printStackTrace(); // 개발자가 보기 위해 꼭 사용 해야 함. 개발자 코드
//			System.out.println("연산 오류 발생 - 다시 한번 시도해 주세요.");
//		} finally {
//			System.out.println("반드시 실행되는 부분");
//		}
    
    // 메서드 호출로 예외처리
    try {
      result = divide(a);
    } catch (Exception e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
    System.out.println(result);
    
    System.out.println("프로그램 끝");
    
  } // end of main ()
  
  public static int divide(int a) throws Exception {
    int result = 0;
    
    result = a / 0;
    System.out.println("연산 완료");
    
    return result;
  }
} // end of class
```