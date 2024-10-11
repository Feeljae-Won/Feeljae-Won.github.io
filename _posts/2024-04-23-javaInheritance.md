---
title: "[Java] 상속 (Inheritance), 추상클래스와 인터페이스"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 상속 (Inheritance), 추상클래스와 인터페이스
- 같은 것 끼리는 extends를 사용 : 클래스가 클래스를 상속, Interface가 Interface를 상속
- Interface -> 클래스 상속 가능 / 클래스 -> Interface 불가능.
- Interface를 클래스가 상속 : impliments (시행하다)

## 추상클래스 - abstract

### 추상 클래스 생성
```java
package ch08interface;

// 추상 클래스 - 추상 메서드를 가지고 있는 클래스
public abstract class AbstractClass {
	
	String name;
	
	// 이름 : 원필재
	
	// **** 출력 ****
	// ** 원필재 : 원필재 **
	// *************
	
	// 추상 메서드는 상속 받은 자식 클래스에서 코드를 작성한다.
	public abstract void print();
	
	public void setAndPrint(String name) {
		this.name = name;
		print();
	}
}
```

### 추상클래스를 상속 받는 클래스 생성 1
```java
package ch08interface;

public class Name1Class extends AbstractClass{

	@Override
	public void print() {
		// TODO Auto-generated method stub
		System.out.println("이름 : " + name);
	}
}
```

### 추상 클래스를 상속 받는 클래스 생성 2
```java
package ch08interface;

public class Name2Class extends AbstractClass {
							
	@Override
	public void print() {
		// TODO Auto-generated method stub
		System.out.println("****** 출력 ******");
		System.out.println("** 이름 : " + name + " **");
		System.out.println("*****************");
	}
}
```

### 상속 받은 클래스를 메인에 변수에 저장해서 사용
```java
package ch08interface;

public class NameExample {
	
	public static void main(String[] args) {
		
		AbstractClass name1 = new Name1Class(); // name1에서 받아옴
		name1.setAndPrint("원필재");
		
		AbstractClass name2 = new Name2Class(); // name2에서 받아옴
		name2.setAndPrint("원필재");
	
	} // end of main()
} // end of class
```

## 인터페이스 - interface

### 인터페이스 생성
```java
package ch08interface;

// 모든 메서드를 추상으로 만든다.
public interface AddCal {
	
	public int add(int a, int b);

}
```

### 더하는 클래스 생성 - 인터페이스 상속
```java
	package ch08interface;
	
	public class AddClass implements AddCal {
	
		@Override
		public int add(int a, int b) {
			// TODO Auto-generated method stub
			return a + b;
		}
	}
```

### 더하고 곱하는 클래스 생성 - 인터페이스 상속
```java
package ch08interface;

public class AddAndMultiClass implements AddCal {

	@Override
	public int add(int a, int b) {
		// TODO Auto-generated method stub
		return (a + b) * 100;
	}
}
```

### 상속 받은 클래스를 생성해 출력
```java
package ch08interface;

public class InterfaceExample {
	public static void main(String[] args) {
		
		AddCal cal = new AddClass();
		System.out.println(cal.add(10, 5));
		cal = new AddAndMultiClass();
		System.out.println(cal.add(10, 5));
		
	} // end of main()
} // end of class
```