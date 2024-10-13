---
title: "[Java] 숫자 바꾸기"
date: 2024-04-17 19:00:00 +0900
categories:
  - docs
  - java
  - algorithm
tags:
  - java
layout: single
---

# Java 알고리즘 - 숫자 바꾸기

```java
package ch04condition;

// 앞에 숫자(x)가 뒤에 숫자(y) 보다 크면 서로 바꾼다.

public class ChangeNoExample {
	public static void main(String[] args) {

		// temp 임시 변수를 활용
		if (x > y) {
			// x = 10, y = 5, temp = 10
			int temp = x; // temp란 '임시로 사용되는' 이라는 뜻.

			// x = 5, y = 5, temp = 10
			x = y;

			// x = 5, y = 10, temp = 10
			y = temp;
		} // end of if

		System.out.println("x = " + x + ", y = " + y);

		// temp를 사용지 않고 x와 y만을 이용해서 숫자를 바꾸세요. : 대입법
		if (x > y) {
			// x = 15, y = 5
			x = x + y;
			// x = 15, y = 10
			y = x - y;
			// x = 5, y = 10
			x = x - y;
		}
		System.out.println("x = " + x + ", y = " + y);
	} // end of main()
} // end of class
```
