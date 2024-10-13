---
title: "[Java] 참조 타입 - 변수 주소, 문자 추출, 문자열 대체, 문자열 잘라내기, 문자열 찾기"
date: 2024-04-17 19:10:00 +0900
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 참조 타입

## 참조형 변수의 주소

```java
MemberInfo memberInfo = new MemberInfo();
MemberInfo mem = memberInfo;

// memberInfo - 200
// mem - 200

mem.tel = "010-1234-2569"
```

## 문자 추출 - .charAt(index)
- 성별 구분
```java
	String ssn = "9506241230123";
	char sex = ssn.charAt(6);
	switch (sex) {
		case "1" :
		case "3" :
			System.out.println("남자입니다.");
			break;
		case "2" :
		case "4" :
			System.out.println("여자입니다.");
			break
}
```

## 문자열 대체 - .replace("찾는 문자열","변경 문자열")

```java
package ch05ref;

/**
 * 문자열 대체 p.160
 */
public class ReplaceExample {
	public static void main(String[] args) {
		
		// String - 문자열 : 문자 배열
		String oldStr = "자바 문자열은 불변입니다. 자바 문자열은 String 입니다.";
		// 한글 자바 -> 영문 JAVA로 변경해 보자. .replace("찾는문자", "바꿀문제") -> 전체를 모두 바꾼다.
		String newStr = oldStr.replace("자바", "JAVA"); // 원문(oldStr)은 바뀌지 않는다.
		
		System.out.println(oldStr);
		System.out.println(newStr);
	} // end of main()
} // end of class
```

## 문자열 잘라내기 - .subString()
```java
package ch05ref;

/**
 * 문자열 잘라내기 p.161
 */
public class SubStringExample {
	public static void main(String[] args) {
		
		String ssn = "880815-1234567";
		System.out.println(ssn);
		System.out.println("문자열 길이 : " + ssn.length());
		
		String firstNum = ssn.substring(0, 6); // 6번째 문자열은 포함하지 않음. (시작 지점, 끝 지점)
		System.out.println(firstNum);
		
		String secondNum = ssn.substring(7); // (시작 지점만 쓰면 끝까지 추출)
		System.out.println(secondNum);
		

		secondNum = ssn.substring(ssn.indexOf("-") + 1); // "-"의 위치를 찾아 + 1 부터 문자열 추출
		System.out.println(secondNum);
		
		// indexOf("1") -> 앞에서 부터 찾아서 "1"이 나오면 그 위치를 리턴 : 4
		// lastIndexOf("1") -> 뒤에서 부터 찾아서 "1"이 나오면 그 위치를 리턴 : 6
	} // end of main()
} // end of class
```

## 문자열 찾기 - .indexOf() .lastIndexOf()
```java
package ch05ref;
/**
 * 문자열 찾기 p.163
 */
public class IndexOfContainsExample {
	public static void main(String[] args) {
		
		// 첫번째 "자바"의 위치 = 0, 두번째 "자바"의 위치 = 9, 마지막 "자바"의 위치 = 18
		String subject = "자바 프로그래밍 자바 프로그래밍 자바 프로그래밍";
		
		
		// indexOf (찾는 글자) -> 앞에서 인덱스 정보를 저장한다. 없으면 -1이 된다.
		int location = subject.indexOf("프로그래밍"); 
		System.out.println(location); // 3번째
		
		// substring(시작 index) -> 시작 index 부터 끝까지 잘라내기를 한다.
		String substring = subject.substring(location);
		System.out.println(substring);
		
		// 과목명(subject)에 자바가 있는지 알아 보고 싶다. 있다 -> index가 0 이상, 없다 -> -1
		location = subject.indexOf("자바");
		System.out.println(location);
		
		// 자바와 관련이 있는지 출력
		if (location != -1) {
			System.out.println("자바와 관련된 책이군요.");
		} else {
			System.out.println("자바와 관련 없는 책이군요.");
		} // if ~ else 문 종료
		
		// 자바가 포함이 되어 있다. -> contains() .  있으면 true, 없으면 false를 돌려준다.
		boolean result = subject.contains("자바");
		// 자바와 관련이 있는지 출력
		if(result) {
			System.out.println("자바와 관련된 책이군요.");
		} else {
			System.out.println("자바와 관련 없는 책이군요.");
		} // if ~ else 문 종료
		
		// 마지막에 나타나는 자바의 위치 찾기
		System.out.println(subject.lastIndexOf("자바"));
		
		// 2번째 자바의 위치 찾기 (보통 for 문을 이용해서 찾음)
		System.out.println(subject.indexOf("자바", subject.indexOf("자바") + 1));
		System.out.println(subject.indexOf("자바", 1));
		
		
		// 파일명 확장자 찾아 보기 - 파일의 특성
		String fileName1 = "c:/my.photo/test.01.jpg";
		String fileName2 = "c:/my.photo/my.jpg";
		
		System.out.println(fileName1.substring(fileName1.lastIndexOf(".") + 1 ));
		System.out.println(fileName2.substring(fileName2.lastIndexOf(".") + 1 ));
		
	} // end of main ()

} // end of class

```