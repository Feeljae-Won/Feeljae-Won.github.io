---
title: "[Java] 키보드 입력 데이터를 변수에 저장 (Scanner & While문)"
date: 2024-04-15 19:10:00 +0900
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 키보드 입력 데이터를 변수에 저장 (Scanner & While문)

## 키보드 입력 데이터를 변수에 저장 (Scanner & While문)
   
```java
// 클래스위 위치 : package
package ch02var;

// 사용하고 있는 프로그램을 포함. 다른 위치에 있는 클래스 ...
// 단, java.lnag의 패키지는 import 하지 않아도 자동으로 되어진다. -> 기본 패키지
import java.util.Scanner;

public class ScannerExample {
	// jvm이 main을 호출하여 사용
	public static void main(String[] args) {
		// 데이터를 입력 받을 때 사용하는 객체(참조형) 변수 선언 + 생성해서 초기화 
		// - (ex : 키보드) (System.in)을 사용 - 파일, 네트워크 등 가능
		Scanner scanner /* 객체가 가지고 있는 주소를 가지고 있다. */ = new Scanner(System.in);
		
		System.out.print("int 타입의 x 값 입력 : ");
		String strX = scanner.nextLine();
		int x = Integer.parseInt(strX);
		
		System.out.print("int 타입의 y 값 입력 : ");
		String strY = scanner.nextLine();
		int y = Integer.parseInt(strY);
		
		int result = x + y;
		System.out.println("x + y : " + result);
		System.out.println();
		
		// ~( 조건을 만족하면 : true) 하는 동안 ( 실행 해라 )
		// while(true) - 무한 반복
		while(true) {
			// 키보드로 데이터 입력
			System.out.print("입력 문자열 : ");
			String data = scanner.nextLine();
			// 빠져나가는 조건을 작성한다. - 입력 받은 데이터가 "q"
			// return - method를 빠져 나간다. System.exit() - 프로그램 종료
			// break - 멈춘다. for, while, switch을 빠져나간다.
			if(data.equals("q")) break;
			
			// 입력한 문자열 출력
			System.out.print("출력 문자열 : " + data);
			// 한줄 여백
			System.out.println();
			// 줄바꿈 문자열 - \n
		} // while 문 끝
		System.out.println("종료");
		
		scanner.close();
	} // main method의 끝
} // class의 끝
```