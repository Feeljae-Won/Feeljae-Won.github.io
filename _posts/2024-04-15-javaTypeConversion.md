---
title: "[Java] 타입 변환"
date: 2024-04-16 19:20:00 +0900
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 타입 변환

## 문자열을 기본 타입으로 변환 
   
```java
package ch02var;

import javax.swing.plaf.synth.SynthToggleButtonUI;

public class PrimitiveAndStringConversionExample {
	public static void main(String[] args) {
		
		// 변수 선언 + 초기값 세팅
		// "10" - 리터럴 (데이터 값) -> String " " ==> 10 - int
		// 문자열의 맨 앞자리 부터 "1" -> 1, 뒤에 더 있으면 * 10 + "0" -> 0
		// int - integer : int 관련된 프로그램을 작성 
		// -> Integer : int wrapper 클래스 ==> int는 Integer와 자동 캐스팅
		//   - 기본형 변수에 대한 처리 등을 만들어 놓은 클래스
		//     byte : Byte, short : Short, int : Integer
		//     char : Character, boolean : Boolean
		int value1 = Integer.parseInt("10");
		System.out.println("value1 : " + value1); // value1 : 10
		
		String str1 = String.valueOf(value1);
		System.out.println(str1); // 10
		System.out.println(str1 instanceof String);  // instanceof : 사례, 경우 > String 타입이 맞는지 확인할 때 : true
		
		System.out.println((value1 + "") instanceof String); // int + ""를 하면 String 타입 : true
		
		// int의 최대 사용 값과 최소 사용 값을 출력해 보세요.
		System.out.println("int의 Max 값은 " + Integer.MAX_VALUE); // int의 Max 값은 2147483647
		System.out.println("int의 Min 값은 " + Integer.MIN_VALUE); // int의 Min 값은 -2147483648
		System.out.println("위에 int 값이 넘어갈 경우 long 타입으로 변환해야 합니다.");
	}
}
```