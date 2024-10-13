---
title: "[Java] 계산기 만들기"
date: 2024-04-19 19:00:00 +0900
categories:
  - docs
  - java
  - algorithm
tags:
  - java
layout: single
---

# Java 알고리즘 - 계산기 만들기

## 클래스 만들기

```java
package ch06class;

public class CalculatorClass {

	// main() 이 없다.
	// 메서드를 작성해서 호출해서 사용해 보자. 선언 부분
	// 더해서 출력하는 메서드
	public void add(int var1, int var2) {
		int result = var1 + var2;
		// System.out.Print(var1 + " " + op + " " + var2 + " = " + result)
		resultPrint(var1, var2, result, "+");
	} // end of add method

	// 빼서 출력하는 메서드
	public void minus(int var1, int var2) {
		int result = var1 - var2;
		resultPrint(var1, var2, result, "-");

	} // end of minus method

	// 곱해서 출력하는 메서드
	// static인 경우 자동으로 미리 올라가낟. resultPrint가 메인 메모리에 올라와야 사용 가능
	public static void multiplication(int var1, int var2) {
		int result = var1 * var2;
		staticResultPrint(var1, var2, result, "*");
	} // end of multiplication method

	// 나누기 출력하는 메서드
	public void divide(int var1, int var2) {
		int result = var1 / var2;
		resultPrint(var1, var2, result, "/");
	} // end of divide method

	// 나머지 출력하는 메서드
	public void remain(int var1, int var2) {
		int result = var1 % var2;
		resultPrint(var1, var2, result, "%");
	} // end of remain method

	// 결과를 출력하는 메소드
	public void resultPrint(int var1, int var2, int result, String op) {
		System.out.println(var1 + " " + op + " " + var2 + " = " + result);
	} // end of resultPrint
	
	// 결과를 출력하는 메소드
	public static void staticResultPrint(int var1, int var2, int result, String op) {
		System.out.println(var1 + " " + op + " " + var2 + " = " + result);
	} // end of resultPrint
}
```

## 만들어진 클래스 사용하기
```java
	package ch06class;
	
	// static import - static을 붙인 메서드를 클래스 이름없이 사용할 수 있도록 하기 위한 import
	import static ch06class.CalculatorClass.multiplication;
	
	public class CalculatorExample {
		public static void main(String[] args) {
			
			// 계산기 사용
			int var1 = 30, var2 = 7;
			
			// static 메소드는 new 하지 않고 사용 - 자주 사용되는 메소드에 static 선언
			// CalculatorClass.multiplication(var1, var2);
			// static import가 되어 있어야 사용 가능
			multiplication(var1, var2);
			
			// CalculatorClass 가져다가 사용하자. -> 메인 메모리에 올려라
			CalculatorClass cal = new CalculatorClass();
			
			// 더하기 처리하고 출력
			cal.add(var1, var2);
			
			// 빼기 처리하고 출력
			cal.minus(var1, var2);
			
			// 곱하기 처리하고 출력
			cal.multiplication(var1, var2);
			
			// 나누기 처리하고 출력
			cal.divide(var1, var2);
			
			// 나머지 처리하고 출력
			cal.remain(var1, var2);
			
		} // end of main()
	} // end of class
```
