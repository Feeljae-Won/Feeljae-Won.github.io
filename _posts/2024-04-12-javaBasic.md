---
title: "[Java] 용어의 이해"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java

## 자바의 특성
  - 호환성
  - 데이터 파악
  - 변수 선언 + 초기화
  - 지역 변수의 사용은 초기화 필수 : 메서드 안에 선언 되어 있는 변수 : 실행이 되야 자리가 생긴다.
  - 전역 변수는 선언하면 기본값이 세팅된다. static, new를 이용해서 메모리에 올린다.
    기본 값 : 숫자 = 0, 참조형 변수 = null, 문자 = ' ' (문자는 공백문자가 있어야 함.), boolean = false

## 용어의 이해
** 자바용어
  1. Package - 위치 (폴더 - 디렉토리) - 소문자로 작성 : 큰 -> 작은
  : 도메인 사용 naver.com -> com.naver.board.controller
  
  2. Class(객체) - 맨 앞자는 대문자로 사용 - 단어 여러개를 말하듯이 작성. 
  한단어의 맨 앞은 대문자로 한다. : PrintInfo
    
  3. 변수 : 맨 앞 자는 소문자로 사용 - 뒤에 단어들의 앞은 대문자로 한다.
      
    1. 기본형 변수 - 고정 길이 - 값을 가지고 있음.
      a. 숫자 - byte, short, int(기본값), long (l) / float(f), double(기본값)
      - int 타입을 double 타입으로 캐스팅 : 10  -> (double) 10 -> 10.0 / 10 * 1.0 -> 10.0
      - String 타입을 int 타입으로 변환 : "10" -> integer.parseInt("10") -> 10
      - int 타입을 String 타입으로 변환 : 10 -> String.vlaueOf(10) or 10 + "" -> "10"
      - scanner.nextLine() -> 입력 받은 것은 모두 문자열 : web으로 통신 받은 것은 모두 문자열 
      - char - 2byte 숫자 (양수) -> int
      - 캐스팅 - 형변환 - 관련이 있는 데이터끼리. 자동 - 큰 -> 작은(손실이 없다.), 강제 - 작 -> 큰 : (타입) 데이터
      
    2. 참조형 변수 - 가변 길이 - 주소를 가지고 있음. : static - Class.변수 / new Class(); // 생성자
      a. 배열 [] - 같은 타입 여러 개(주소는 1개) - index 사용 ex - scores[3].length
              배열의 모든 데이터 출력
          for문 :  for(int i = 0; i < scores.length; i++) System.out.println(scores[i]);
          foreach문(향상된 for문) :  for(score : scores) System.out.println(scores[i]); // 변수 1개를 더 선언하여 사용
          데이터가 나중에 생기는 경우. 인덱스 사용 : int [] scores = new int[10];
                          ex - int [] scores = {100, 90, 80}; == new int[] {100,90,80};
                        
        ex - 1 ~ 10 까지 숫자를 더해 보세요. : 
        ```java
          int sum = 0; 
          for(int i = 1; i <= 10; i++) sum += i; // ( sum = sum +1 같은 의미)
        ```

        ex - 점수 합계와 평균을 구해 보세요 : 
        ```java
          int sum = 0; int [] scores = {100, 90, 80};
          
          // 합계 구하기
          for(int i = 1; i <= 10; i++) sum += scores[i]; // for 문 사용
          for(int score : scores) sum += scores[i]; // foreach 문 사용
          
          // 평균 구하기 (int)
          int avg = sum / scores.length; -> 90
          // 평균 구하기 (double)
          double avg = ((double) sum) / scores.length; -> 90.0 // sum을 (double)을 사용하여 강제 캐스팅
        ```

      b. class - 변수들, 메서드들() 
        - 다른 타입의 여러개를 저장할 수 있다. : 연관이 있는 여러 개
      
      c. String - char[] : index 관련 처리, length() 를 가지고 있음.
        - .charAt(3) - 위치(3)에 해당하는 문자열
        - .length() - 문자열 길이
        - .replace() - 데이터 바꾸기
        - .indexOf - 찾는 글자의 위치 찾기
        - .contains() - 포함되어 있는지 확인,
        - .substring() - 문자 잘라내기
        - .lastIndexOf() - 뒤에 부터 위치 찾기
    
    3. 컬렉션 & Map
      - 자바에서는 컬렉션 프레임워크를 통해 다양한 자료구조를 제공합니다. 
      이 프레임워크는 데이터를 효율적으로 관리하기 위한 클래스들의 집합입니다. 

        • List:
          □ 순서가 있는 데이터를 저장하는 인터페이스입니다.
          □ 중복된 값을 허용하며, 인덱스로 객체를 관리합니다.
          □ 대표적인 구현 클래스: ArrayList, LinkedList, Vector

        • Set:
          □ 순서가 없는 데이터를 저장하는 인터페이스입니다.
          □ 중복된 값을 허용하지 않습니다.
          □ 대표적인 구현 클래스: HashSet, TreeSet

        • Map:
          □ 키(key)와 값(value) 쌍으로 데이터를 저장하는 인터페이스입니다.
          □ 키는 중복되지 않으며, 값은 중복 저장 가능합니다.
          □ 대표적인 구현 클래스: HashMap, TreeMap

      - 컬렉션 프레임워크를 사용하여 데이터를 효율적으로 관리할 수 있습니다. 
      각 인터페이스와 클래스는 다양한 메서드를 제공하여 데이터 추가, 삭제, 검색, 저장 등을 수행할 수 있습니다. 😊
      
    4. 연산자
      a. % - 배수를 찾아낼 때 사용. 3의 배수 : num % 3 == 0
      b. i++ (후증가), ++i (선증가), i-- (후감소), --i (선감소)
        ex - 1증가 시키고 출력한다.
          i = i + 1; == i += 1; == i++;
          System.out.prinln(i)
          
          -- System.out.println(++i);
        
      c. 삼항 연산자(조건 연산자) : (조건) ? True : false
                (조건) ? True. (조건) ? Ture : false
      d. && 연산자 : 둘 다 True 일 경우 True
      e. | | 연산자 :  둘 중 1개가 True 면 True
      f. instanceof : 타입이 같은지 물어볼 때
    
    5. 제어문
      a. 조건문 - if, switch
        - if - if ~ true 면 실행, else 면 false 조건 실행, else if 면 조건문 안에 조건문 생성 가능.
        - switch - 라벨을 이용해 이동하고 아래로 실행
          • switch (변수 & 수식) { case 값 : 처리문; break;} // break 를 사용하면 다음 case로 넘어가지 않고 종료 됨. 
          // break - switch, for ,while 문을 빠져나감.
      b. 반복문 - for, while
        - for - 규칙, 반복 횟수 정해져 있는 조건
          • for ( 초기값, 초기값 ; 반복조건 ; 증감, 증감) for ( ; ; ) // 초기값은 int 타입
          • foreach - for ( 변수 : 변수들 [ ]  ), 컬렉션도 사용 가능. // 향상된 for == foreach
        - while - while(조건) - while(true) : 무한 반복 // 메뉴 선택 처리하기 위해 사용 - Controller
  
    6. 패키지
      a. java.lang - 자주 import 되는 패키지
    
    
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