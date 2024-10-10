---
title: "[Java] 변수의 탕입"
categories:
  - docs
  - java
layout: single
---

# Java 변수의 타입--
title: "[Java] 변수의 탕입"
categories:
  - docs
    - java
    layout: single
    ---

    # Java 변수의 타입

## 정수 타입
    - 변수의 형태 = 데이터의 형태
        A. 타입 변수명; --> 변수 선언
        B. 타입 메서드명(); --> 메서드 선언 - 메서드 타입에는 변수 타입 + void
 
    - 타입
        A. 기본형 타입 - 이미 정해져 있는 고정 길이 타입. 값이 저장 된다.
            i. 숫자
                1. 정수 - 고정 소수점 형식(소수점이 없다.) : 부호 + 유효숫자
                - Byte - 1 Byte(8bit) : 1과 0으로 이루어진 데이터 > 12
                - Short - 2 byte(16bit) >12
                - Int - 4 byte(32bit) : +-17억 내 숫자 데이터 > 가장 기본으로 사용 >12
                - Long - 8 byte(64bit) : int 보다 큰 숫자 대이터 > 12L (long은 L을 붙여야 함.)

```java
package ch02var;

public class LongExample {
	public static void main(String[] args) {
		
		// 10 -> int 리터럴로 선언 -> long 타입 변수에 저장
		//  : 타입이 서로 틀린 곳에 데이터는 전달하는 것을 '캐스팅'이라고 한다.
		//  : 작은(int) -> 큰(long) - 데이터 손실이 일어나지 않음. '자동 캐스팅'
		//  : 큰(long) - > 작은(int) - 데이터 손실이 일어남.
		long var1 = 10;
		
		//  : 큰(long) - > 작은(int) - 데이터 손실이 일어날 수 있다. '강제 캐스팅'
		// int varInt = (int) var1; // 전달 데이터 앞에 변환할 타입을 선언 (데이터 손실이 일어나도 감수하겠다.)
		
		
		long var2 = 20L;
		
		// long var3 = 1000000000000;  -> int로 리터럴 선언 : 범위 초과 되어 오류
		// int 초과되는 숫자는 뒤에 L을 붙여서 long 타입으로 변환시킨다.
		long var4 = 1_000_000_000_000L	;
		
		System.out.println(var1); // 10
		System.out.println(var2); // 20
		System.out.println(var4); // 1000000000000

	}
}
```

## 실수 타입
    2. 실수 - 부동 소수점 형식(소수점이 있다.) : 부호 + 지수 + 유효숫자
     - Float - 4 byte  >> 1.2F (float은 F를 붙여야 함.
```java
package ch02var;

public class FloatDoubleExapmle {
	public static void main(String[] args) {
		
		float var1 = 0.1234567890123456789f;
		// float var1 = 0.1234567890123456789f;  
		// double var2 = 0.1234567890123456789;
		
		double var2 = 0.1234567890123456789;
		// float가 혀용하는 자리수가 있다. 그것보다 넘치면 나머지는 자른다.
		System.out.println(var1);
		System.out.println(var2);
		
		double var3 = 3e6;
		System.out.println(var3);
		double var4 = 2e-3;
		System.out.println(var4);
	}
}
```

## 문자 타입
   1. Char - 2byte : 양수(+)로 운영.  (A : 65)

```java
package ch02var;

public class CharExample {
	public static void main(String[] args) {
		
		char c1 = 'A'; // 문자 타입은 ''안에 한 글자를 반드시 입력해야 한다.
		char c2 = 65; // char 문자 타입인 경우 0 이상의 숫자로 운영 된다. (2 byte 크기)
		
		System.out.println(c1);
		System.out.println(c2);  // c2 타입은 문자 -> 출력은 문자
		System.out.println(c2 + 1);  // char + int -> int 타입으로 변환 -> 숫자 출력
		System.out.println((char)(c2 + 1));  // char + int -> int 타입으로 변환 -> 숫자 출력
		System.out.println((int)c2);
		
		char c3 = '가';
		char c4 = 44032;
		
		System.out.println(c3);
		System.out.println(c4);
		System.out.println((char)(c4 + 1056));
	}
}
```

## 논리 타입
    1. Boolean : true / false - 1 byte
```java
package ch02var;

public class BooleanExample {
	public static void main(String[] args) {
		
		// 처리를 세울 때 사용되는 변수 선언. 초기값을 true로 넣었다.
		boolean stop = true;
		System.out.println(stop);
		
		if (stop) { 	// 만약에 'stop'(=true)이면 다음 한개 처리
			System.out.println("중지합니다.");
		} else {
			System.out.println("시작합니다.");
		}
		
		// 처리문 한 개인 경우
		if (stop)  	// 만약에 'stop'(=true)이면 다음 한개 처리
			System.out.println("중지합니다.");
		else 
			System.out.println("시작합니다.");		// if 문 끝
		
		int x = 10;
		boolean result1 = (x == 20);		// 변수 x의 값은 20과 같은가?
		boolean result2 = (x != 20);		// 변수 x의 값은 20과 다른가?
		System.out.println(result1);
		// 값을 딱 한번만 사용하는 경우는 변수에 넣지 않는다.
		System.out.println(x == 20);
		System.out.println(result2);
		
	}
}
```

## 참조형 타입
    B. 참조형 타입 - 개발자가 만들어서 사용하는 타입. 가변 길이 타입. 주소가 저장된다. 주소는 4 byte 정도를 저장함.
        i. 문자열 - String : char[]
        ii. 배열 - 동일한 타입 여러 개 : []
        iii. 클래스 - 다른 타입의 변수 여러 개 선언 가능
        iv. 컬렉션과 Map