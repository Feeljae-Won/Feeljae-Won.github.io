---
title: "[Java] 싱글톤(Singleton) 패턴"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 싱글톤(Singleton) 패턴
- 딱 한개의 객체만 운영이 되게하는 시스템 -> 서버

- 생성자를 만든다. -> private : 같은 클래스에서만 동작 -> new
- 클래스 내부에서 new해서 private 변수에 저장해 놓는다. -> 사용하기 위한 메서드( getInstance() )를 호출해서 사용한다.

## Singleton 생성
```java
package ch06class;

public class Singleton {
	
	// private 접근 권한을 갖는 정적 필드 선언과 초기화
	private static Singleton singleton = new Singleton();
	
	// private 접근 권한을 갖는 생성자 선언
	private Singleton() {}
	
	// public 접근 권한을 갖는 정적 메소드 선언
	// static 아닌 요소들은 6번 째 줄에서 생성되어 올라간다.
	
	// Singleton 을 사용하려면 변수 선언하고 getInstance() 호출해서 사용하세요.
	// public static Singleton getSingleton() { return singleton;}
	
	public static Singleton getInstance() { return singleton;}
	
	public void print() {System.out.println("Singleton"); }
}
```

## Singleton 사용
```java
package ch06class;

public class SingletonExample {
	public static void main(String[] args) {
		
		/*
		 * Singleton obj1 = new Singleton(); // 컴파일 에러 
		 * Singleton obj2 = new Singleton(); // 컴파일 에러
		 */
			
		// 싱글톤 객체가 한번만 생성이된 것을 사용한다.
		Singleton obj1 = Singleton.getInstance();
		obj1.print();
		Singleton obj2 = Singleton.getInstance();
		obj2.print();
		
		System.out.println(obj1 == obj2);
		
		// 같은 주소 값이 나오게 된다.
		System.out.println(System.identityHashCode(obj1));
		System.out.println(System.identityHashCode(obj2));	
		
		// 정적 메소드를 호출해서 싱글톤 객체 얻음
//		Singleton obj1 = Singleton.getInstance();
//		Singleton obj2 = Singleton.getInstance();
		
		// 동일한 객체 참조하는지 확인
		if ( obj1 == obj2 ) {
			System.out.println("같은 Singleton 객체 입니다.");
		} else {
			System.out.println("다른 Singleton 객체 입니다.");
		}
		
	} // end of main()

} // end of class
```
