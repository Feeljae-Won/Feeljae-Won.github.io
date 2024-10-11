---
title: "[Java] 용어의 이해"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java 용어의 이해

## 용어의 이해
** 자바용어
  1. Package - 위치 (폴더 - 디렉토리) - 소문자로 작성 : 큰 -> 작은
  : 도메인 사용 naver.com -> com.naver.board.controller
  
  
  2. Class(객체) - 맨 앞자는 대문자로 사용 - 단어 여러개를 말하듯이 작성. 
  한단어의 맨 앞은 대문자로 한다. : PrintInfo
    
    - 변수 : 맨 앞 자는 소문자로 사용 - 뒤에 단어들의 앞은 대문자로 한다.
      
      a. 기본형 변수 - 값, 고정길이 (모두 소문자로 이루어짐)
        1) 숫자
        □ 정수 : 소수점이 고정 (맨 뒤에 고정 : 소수점 없음) - byte - short - int(*) - long(l)
        □ 실수 : 소수점이 부동 (움직인다. : 소수점이 있음) - float(f) - double(*)
      
      b. 참조형 변수 - 주소, 가변길이 (첫 글자가 대문자로 이루어짐)
        1) 배열 : 같은 타입 여러 개 [ ] - String [ ] args
        2) 클래스(class) : 변수 들 / 메서드 들 ( )- 다른 타입  여러 개	
        3) String : 문자열 - char[ ]
        4) 컬렉션(value, 데이터만 저장) & Map(key - value, 위치와 데이터를 저장)
    
    - 메서드 ( ) : 맨 앞 자는 소문자로 사용 - 뒤에 단어들의 앞은 대문자로 한다.
    
  System(클래스).out(변수).println(메서드)("test");

```java
// package - 꾸러미(묶음) : 위치 = 폴더
// class - 방 : 파일 (~.java)

package thisisjava;

// public - 공통, 공유 : 다른 장소(package)에서도 사용 가능하다.
public class Hello {

  // public - 공동, 공유 : 다른 장소(package)에서도 사용 가능하다.
  // static - 정적인, 고정된 <-> non-static(아무 표시가 없음) -> new (새로 만들 때 : 생성자)
  //        - 자동으로 메인 메모리에 올라가고 쫓겨나지 않아서 주소가 고정되어 있다.
  //        - 사용하려면 Hello(클래스, 패키지).main()로 사용한다. (JVM이 사용)
  // void   - 비어있다. : 메서드(처리 명령어 들의 집합) 처리 후 돌려 받는 것이 없다.
  // main   - 주된, 주요한 : 시작되는 부분의 처리문이 있는 곳. 뒤에 ()이 있다.
  //        - main에서 처리해야할 명령어는 여러개로 묶은 한개로 만들기 위해서 {~~~}
  //        - main 메서드에 처리할 때 사용되는 데이터를 () tkdldp sjgdjwnsek.
  // String - 문자열. 끈 줄, 이어지다. "" 안에 있는 데이터 또는 new String()
  // []     - 여러개를 의미. 베열 - 똑같은 데이터 타입이 여러개 나열 되어 있는 선언
  // args   - arguments의 약자. 논재아, 논의, 논거 - if 문의 결정되게 한느 근거 데이터
  
  // -- 이곳이 처음 시작하는 부분 : JVM이 처음 찾아서 실행하는 부분
  public static void main(String[] args) {
    // System - 체계, 컴퓨터 조직 : 컴퓨터 시스템을 의미
    // System.out - System. 안에 out이 있다. (.의 의미)
    // out - 표준 출력(모니터) 처리를 담고 있는 변수 : Printstream
    System.out.println("Hello! java");
  }
}
```

## 주석
```java
// 주석
/**
  * 외부에서 보이는 범위 주속으로 작성된다.(클래스에 해당)
  * 문서를 만들 때도 사용.
  */

/*
  * 외부에서 보이지 않는 범위 주석 (소스를 보는 사람)
  */

// 이후 부터 줄이 끝날 때까지 주석 (한줄 주석)
```