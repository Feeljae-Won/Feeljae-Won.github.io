---
title: "[Java] 클래스 - Class"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# 클래스 (Class)
- 클래스 또는 메서드를 만드는 목적
	1) 반복 된다. - 클래스는 다른 패키지에서 사용할 수 있음. 메서드는 클래스 안에 개인이 쓰기 위한 코드
	2) 복잡 하다. 

- 변수들과 메서드들() : 클래스
	
-  객체 생성 
	- static : 변수, 메서드() -> class명.변수, class명.메서드()
	- new 생성자() -> 변수 Member men = new Member()
-  생성자 
	- 리턴 타입 없음. 클래스 이름과 동일하게 만든다. 파라미터는 마음대로
	- 생성자는 non -static 변수의 파라메터로 부터 전달 받은 초기값을 세팅하기 위해
	
- 초기화 블록 - { ~ }, static { ~ } : 자동으로 생성. 전달 받은 값이 없다. 리터럴 값을 세팅
- 접근 제한자 : public (기본) - protected (보호한다) - private (한정적)
- 그외 제한자 : final(변경이 불가)


## 접근 제한자
- 접근 제한자
- 코딩할 때 main에 작성
- public - static void main(String[] args) { ~ }
- protected - 같은 패키지 내에서 상속은 가능
- (default) - 아무것도 쓰지 않음
- private - 같은 클래스 안에서만 사용
- 하드디스크 파일 (클래스) -> 메인 메모리 (객체 = 인스턴스(예제)) : 변수들, 메서드들
	* 로딩 = 인스턴스화
	* 변수들 또는 메서드들 : 접근 제한자 + 제한제 + 타입 변수명 or 메서드명()

|접근 제한자|제한 대상|제한 범위|
|---|---|---|
|`public`|클래스, 필드(변수), 생성자, 메서드|없음|
|`protected`|변수, 생성자, 메서드|같은 패키지 또는 자식 객체만 사용 가능|
|`(default)`|클래스, 변수, 생성자, 메서드|같은 패키지|
|`private`|필드, 생성자, 메서드|객체 내부|

## final 제한자
- 변하지 않는다.
	* 클래스, 변수, 메서드() 앞에 붙힐 수 있다.
	* 클래스 : 상속을 받지 못한다.
	* 변수 : 값을 재정의 할 수 없다. 값을 넣을 수 없다.
	* 메서드 : 상속 받은 메서드를 재정의 할 수 없다.

## 메서드
- 처리문 -> 호출해서 사용한다.
	* 특별한 메서드
		* public String toString() { return 문자열; }
			* 참조형 변수 -> 클래스명@16진수값 : Object 클래스 안에 코드 작성되어 있음. 출력할 때 자동으로 호출한다.



## `MemberExample.java` 와 `Member.java`를 이용해 클래스 사용하기

### Member.java
```java
package ch06class;

/**
 * 회원을 관리해주는 데이터 객체로 사용. 아이디, 이름, 나이, 클래스 이름
 */

public class Member {

	// 데이터를 저장하는 변수들을 가지고 있다.
	// 클래스의 구성원으로 가지고 있다. member 변수 == 전역 변수
	// Static 변수 - 자동으로 올라간다. Member.className 으로 사용
	static String className;

	// non-static 변수 - new 해서 올린다. Member m1 = new Member(); m1.id; -> 인스턴스 변수
	String id; // 기본 값 - null
	String name; // 기본 값 - null
	int age; // 기본 값 - 0

	// new Member();
	// - 모든 클래스는 생성자를 만들지 않으면 컴파일 할 때 자동으로 기본 생성자 - 클래스 이름()를 만든다.
	// 생성자를 작성하는 목적은 변수의 초기 데이터를 세팅할 때 사용된다.

	// 초기화 블록 - Member 클래스 이름이 불려지면 자동으로 실행되는 처리문
	// static 초기화 블록 - 클래스 이름이 불려지면 자동으로 실행 
	//	- 딱 한번만 실행 : static 변수 초기값 세팅할 때 주로 사용.
	// 값을 바로 대입 할 때 사용
	static {
		System.out.println("static 초기화 블록 처리 : 딱 한번 ----------");
		className = "Member";
	}

	// 초기화 블록 - new 할 때마다 자동으로 실행 
	//	- non-static 변수 초기값 세팅
	{
		System.out.println("non-static 초기화 블록 처리 : new 할 때 마다 ----------");
	}

	// 생성자 - 값을 전달 받아서 non-static 변수의 값을 세팅하기 위해서 사용 - new 할 때 한번만 실행

	// 기본 생성자 - 기본 값으로 데이터를 세팅해 주는 생성자
	// - 1. 리턴 타입 없음.(new)
	// - 2. 클래스 이름과 같다.
	// :: 기본 값 세팅을 하지 않으면 생략 가능 -> Compiler가 자동으로 만들어 준다.
	public Member() {
		System.out.println("기본 생성자 실행 - new 할 때마다 기본생성자()");

		// 프로그램 동작 전에 기본 값 세팅, 파라미터로 받지 않음. 컴파일러가 자동으로 생성됨.
		id = "test";
		name = "홍길동";
		age = 30;
	}
	// 생성자 - non-static 변수 초기화 하기 위해 사용한다.
	public Member(String id, String name, int age) {
		this.id = id;
		this.name = name;
		this.age = age;
	}
}
```

### MemberExample.java
```java
package ch06class;
public class MemberExample {
	public static void main(String[] args) {
		
		// Member 클래스를 불러와서 사용해 보자. 생성자 호출
		Member m1 = new Member();	// static을 자동으로 클래스 이름이 불려지면 올라간다.
		System.out.println(m1.name); // Member 클래스에 설정한 변수의 이름이 불러온다.
		
		Member m2 = new Member();	// static을 자동으로 클래스 이름이 불려지면 올라간다.
		System.out.println(m2.name); // Member 클래스에 설정한 변수의 이름이 불러온다.
		System.out.println(Member.className);
		// non-static 이기 때문에 경고문이 생기나 오류가 나지는 않음.
		System.out.println(m1.className); 
	
		// 생성자를 사용 데이터 초기화
		Member m3 = new Member("admin", "원필재", 33);
		System.out.println(m3.name);
	} // end of main()
} // end of class
```

