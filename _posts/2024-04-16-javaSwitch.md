---
title: "[Java] 조건문 (switch문) 예제"
date: 2024-04-16 19:20:00 +0900
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 조건문

## switch문
- Switch - == : 비연속 데이터 : switch(변수) { case 값 : ~~ ; default : ~~~ }

### switch문 예제
```java
package ch04condition;

import java.util.Random;

public class SwitcchExample {
	public static void main(String[] args) {
		
		// 주사위를 던졌다. 1 ~ 6 중에 하나의 숫자가 랜덤으로 나타나게 된다.
		// 0.0 * 6 = 0.0 = > 0, 0.9 * 6 = 5.4 = > 5 (랜덤으로 돌릴 숫자 개수를 곱하면 된다. 1부터 시작할 땐 +1)
		// java - Math.random / Random
		// System.out.println((int)(Math.random()*45) + 1);
		// System.out.println((int)((Math.random()*6) + 1));
		
		int num = ((int)((Math.random()*6) + 1)); // (int)(Math.random()*6) - 강제 캐스팅
		
		// 조건 문에 의해서 처리해 보자. == 비교 : if / switch
		// switch(변수나 변수를 포함한 수식) { case 값 : 처리문; ... }
		// 변수나 변수를 포함한 수식 = 값 조건에 맞는 case 로 이동해서 계속 아래로 실행
		switch(num) {
		// 라벨 : -> 이동 처리하는 표시
		case 1:
			System.out.println(num + "번이 나왔습니다.");
			// break - switch, for, while 문을 빠져 나간다. if 문은 아님.
			break;	
		 case 2:
			System.out.println(num + "번이 나왔습니다.");
			break;	
		case 3:
			System.out.println(num + "번이 나왔습니다.");
			break;
		case 4:
			System.out.println(num + "번이 나왔습니다.");
			break;
		case 5:
			System.out.println(num + "번이 나왔습니다.");
			break;
		default:
			System.out.println(num + "번이 나왔습니다.");
			
		} // end of switch
		
	} // end of main()

} // end of class
```