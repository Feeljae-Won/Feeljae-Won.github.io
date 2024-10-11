---
title: "[Java] 연산자"
categories:
  - docs
  - java
layout: single
---

# Java 연산자

## 비교 연산자 (Compare Operaor)
   
```java
package ch03op;

public class CompareOperatorExample {
	public static void main(String[] args) {
	
		int varInt = 10;
		String str1 = "10";
		// == : 같다.
		System.out.println(varInt); // 10
		System.out.println(str1); // "10"
		// System.out.println(varInt == str1); // 연관이 있는 것 끼리 연산을 시도해야 한다. (숫자 == 글자 -> 연산 안됨.)
		
		String str2 = "10";
		System.out.println(str1 == str2); // true
		
		String str3 = new String("10");
		System.out.println(str3); // 10
		System.out.println(str1 == str3); // false -> String은 참조형 변수로 둘의 텍스트 모양은 같지만 저장 위치가 달라 false
		// str1과 str3의 주소관련 데이터 출력하시오.
		System.out.println("str1의 주소 값 : " + str1.hashCode()); // 1567
		System.out.println("str3의 주소 값 : " + str3.hashCode()); // 1567
		System.out.println("str1의 주소 값 : " + System.identityHashCode(str1)); // 2001049719
		System.out.println("str2의 주소 값 : " + System.identityHashCode(str2)); // 2001049719
		System.out.println("str3의 주소 값 : " + System.identityHashCode(str3)); // 1528902577
		
		// 문자열인 경우 주소를 사용하는 해시함수에 값을 넣어서 그것을 가지고 주소로 사용한다.
		// 값이 같으면 같은 주소를 가지게 된다. (메모리 효율성 때문 - 참조형 데이터는 같은 값은 덮어 써 버림.)
		// new 해서 생성된 것은 서로 다른 주소를 가진다.
		// 값이 같으면 같다고 처리해야 한다. 이 때 사용되는 메서드가 equals() 이다.
		System.out.println(str1.equals(str3)); // true
		System.out.println(str1.equals(str2)); // true
		
		// 값이 같은 참조형 변수를 선언하면 같은 리터럴 값의 주소를 가지게 된다. str1은 str3의 리터럴 값 주소를 가지고 있음.
		str1 = str3;
		System.out.println(str1 == str3); // true
	}
}

```

## 논리 연산자 (Logical Operaor)
   
```java
package ch03op;

public class LogicalOperatorExample {
	
	public static void main(String[] args) {
		// and 모두 true 면 true, 하나라도 false면 false - & / &&(*)
		// or 논리 중 한개라도 true 면 true - | / ||(*)
		// xor - ^ : true 홀수 개
		// not (논리 부정) - !
		
		String name = null; // 참조형 변수인데 주소가 없음.
		// name.equals("lee") -> name이 null이면 찾을 곳이 없어서 오류
		// System.out.println(name != null & name.equals("lee")); // 오류
		System.out.println(name != null && name.equals("lee")); // false -> 첫 논리가 false여서 뒤에 논리는 계산하지 않음.
		
	}
}
```

## 삼항 연산자 (Conditional Operaor)
   
```java
package ch03op;

public class ConditionalOperationExample {
	public static void main(String[] args) {
	
	int score = 83;
	// 등급 계산 -> 문자 'A'
	// : -> 그렇지 않으면
	// score가 90이상 이면 'A'
	// score가 80이상 이면 'B'
	// 그 외는 'C'
	// 3항 연산자 (항목이 3개다.) - 조건? true 값 : false 값
	char grade = (score >= 90) ? 'A' : ((score >= 80) ? 'B' : 'C');
	System.out.println(score + "점은 " + grade + "등급 입니다.");
	
	// if ~ else를 이용한 삼항 연산
	grade = ' ';
	if(score >= 90) grade = 'A';
		else if(score >= 80) grade = 'B';
		else if(score >= 70) grade = 'C';
			else grade = 'D';
	System.out.println(grade);
	
	}
}
```