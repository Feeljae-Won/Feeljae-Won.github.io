---
title: "[Java] 반복문 (while, do while) 예제"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 반복문

## while문
- 무한 반복 : while (true) { 처리문들(데이터변경) ;  빠져나가는 조건 ; 처리문들 ; }

## while문 예제
- 메뉴 - 1. 게시판 2. 공지사항. 3.상품 4.로그인 0. 종료
		1 / 2 / 3 / 4 - 해당 메뉴를 처리하였습니다. 라는 메시지를 출력한다.
		0 - 헤어지는 인사를 하고 프로그램을 종료한다.
		
		- 무한 반복
			§ 메뉴 출력 
			§ 메뉴 키보드로 입력
			§ 입력한 메뉴를 처리 - switch : 문자열 비교 가능(String)
			메뉴 이 외(default)의 데이터를 "잘못된 메튜를 입력하셨습니다. 다시 입력해 주세요."
			
- 프로그램 종료 - System.exit(0); -> 0 은 정상적인 종료

```java
package ch04condition;

import java.util.Scanner;

public class Main_1 {
	public static void main(String[] args) {
		// 업무 프로그램 시작
		// 키보드로 입력 받는 객체 선언
		Scanner scanner = new Scanner(System.in);
		
		// 라벨을 붙인다.
		// whileLoop:
		while (true) {
			// 메뉴 출력 메뉴 - 1. 게시판 2. 공지사항. 3.상품 4.로그인 0. 종료
			System.out.println("1. 게시판 2. 공지사항. 3.상품 4.로그인 0. 종료");
			// 메뉴 입력
			String menu = scanner.nextLine();
			// 입력한 내용을 처리
			switch (menu) {
			case "1":
				System.out.println("게시판을 처리하였습니다.");
				break;
			case "2":
				System.out.println("공지사항을 처리하였습니다.");
				break;
			case "3":
				System.out.println("상품을 처리하였습니다.");
				break;
			case "4":
				System.out.println("로그인을 처리하였습니다.");
				break;
			case "0": // 프로그램 종료
				System.out.println("프로그램을 종료합니다.");
				scanner.close();
				// break whileLoop; // whileLoop 블록을 빠져 나간다.
				System.exit(0);
			default:
				System.out.println("잘못된 메뉴를 선택하셨습니다.\n[1~4, 0]을 입력하셔야 합니다.");

			} // end of switch
		} // end of while
	} // end of main()
} // end of class
```

### 조건 반복
- 1 부터 10까지 출력하는 프로그램

```java
package ch04condition;

import java.util.Scanner;

// 4.5 while 문 (p.129)
// 1 ~ 10 까지 출력하는 프로그램 작성

public class PrintFrom1To10Example_1 {
	public static void main(String[] args) {

		// for 문을 사용한 프로그램
		for (int i = 1; i <= 10; i++)
			System.out.print(i + " ");
		System.out.println();

		// while 문을 사용한 프로그램
		// 변수 선언 ( for 문 안에 있는 i는 지역 변수 이므로 전역 변수인 i와 오류나지 않음.)
		int i = 1;

		// for(int i = 1; i <= 10; i++) System.out.print(i + " "); // 변수 선언 후 같은 이름의 지역
		// 변수를 선언하면 오류
		for (; i <= 10;)
			System.out.print(i++ + " ");
		System.out.println();

		
		// 위에 for 문이 끝나면 i = 10
		// 변수 다시 선언 - 초기값 세팅
		i = 1;

		// start of while - 1 ~ 10 까지 출력
		while (i <= 10)
			System.out.print(i++ + " ");
		System.out.println(i); // while 이 끝난 i = 11

		
		// String을 활용한 while 문
		// String은 참조형 변수이기 때문에 위치를 가진다.
		// "" 쓴 이유는 초기값이 없기 때문에 ""로 선언.
		String menu = "";

		Scanner scanner = new Scanner(System.in);

//		// while(빠져나가는 조건) = 조건에 맞지 않으면 빠져 나간다.
//		while (!menu.equals("0")) { // 0이면 빠져 나간다. = 0이 아니면 반복 처리한다.
//			System.out.println("메뉴를 입력하세요.");
//			menu = scanner.nextLine();
//			if (!menu.equals("0"))
//				System.out.println("처리");
//		} // end of while
		
		String menu1 = null;
		
		// menu1이 null 이거나 또는 munu1이 null이 아니고 "0"이 아니면 실행하자.
		// while (menu1 == null || (!(menu1 == null) && menu1.equals("0"))) { -> 오류
		// while (!(menu1 == null) ? !menu1.equals("0"):true) {
		while ((menu1 == null) ? true : !(menu1.equals("0"))) {
			System.out.println("메뉴를 입력하세요.");
			menu1 = scanner.nextLine();
			if (!menu1.equals("0") && !menu.equals(null))
				System.out.println("처리");
		} // end of while
		
		scanner.close();
		
		System.out.println("종료");

	} // end of main()

} // end of class
```

## Do While문
```java
package ch04condition;

import java.util.Scanner;

// do-while 문 p.133

public class DoWhileExample {
	public static void main(String[] args) {

		System.out.println("메시지를 입력하세요.");
		System.out.println("프로그램을 종료하려면 \"q\"를 입력하세요.");

		Scanner scanner = new Scanner(System.in);
		String inputString;

		do {
			System.out.print(" > ");
			inputString = scanner.nextLine();
			System.out.println(inputString);
		} while (!inputString.equals("q"));

		System.out.println();
		System.out.println("프로그램 종료.");
		
		scanner.close();
	} // end of main()
} // end of class
```