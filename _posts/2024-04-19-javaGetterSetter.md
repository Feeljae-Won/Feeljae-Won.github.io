---
title: "[Java] Getter와 Setter"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# Java Getter와 Setter
- Getter : 데이터를 불러오기 위해 생성한다.
- Setter : 데이터를 저장하기 위해 생성한다.
- toString() : 데이터를 정상적으로 저장하고 불러오는지 확인하기 위해 생성한다.

## Getter & Setter & toString() 생성하기
```java
package ch06class;

// 일반 게시판에 데이터를 저장하는 객체
// -> BoardVO(데이터 저장) == BoardDTO(데이터 전달) == Board
public class Board {

	// 변수 선언 - 데이터 저장
	// private - 개인적인 - 같은 클래스에서만 사용되는 변수 - 만들어서 직접 접근이 안되도록 한다.
	private long no;
	private String title;
	private String content;
	private String writer;

	// 맨 처음 데이터 세팅하기 - 생성자 작성 - 필요하면 만든다.

	// 데이터를 넣는 setter 메서드(), 데이터를 가져가는 getter 메서드()
	// getter 만들기 - 데이터 저장
	public long getNo() {
		// 사용, no -> 위로 올라가면서 변수를 찾는다. : 지역 -> 전역
		// this. -> 객체 안에 변수 no 찾기 : 전역
		return this.no;
	}

	// setter 만들기 - 데이터 넣기
	public void setNo(long no) {this.no = no;}

	// getter 만들기 - 데이터 저장
	public String getTitle() {return this.title;}
	// setter 만들기 - 데이터 넣기
	public void setTitle(String title) {this.title = title;}

	// getter 만들기 - 데이터 저장
	public String getContent() {return this.content;}
	// setter 만들기 - 데이터 넣기
	public void setContent(String content) {this.content = content;}

	// getter 만들기 - 데이터 저장
	public String getWriter() {return this.writer;}
	// setter 만들기 - 데이터 넣기
	public void setWriter(String writer) {this.writer = writer;	}
	
	// 출력할 때 자동으로 호출되는 메소드 : toString()
	// 상속 받았지만 부모 클래스를 우선 호출 하게 된다.
	// 주로 데이터 확인용으로 사용.
	public String toString() {
		return "Board[no=" + no + ", title=" + title + ", content="	+ content + ", writer=" + writer + "]";
	}

} // end of class
```

## Getter & Setter 사용
```java
package ch06class;

public class BoardExample {
	
	public static void main(String[] args) {
		
		// Board 객체 사용해 보기 - 일반 게시판의 데이터를 한꺼번에 처리하고자 할 때
		Board board = new Board();
		System.out.println(board); // -> 데이터가 없으므로 해쉬코드가 나옴. ch06class.Board@372f7a8d
		
		
		// 데이터 no = 10, title = "자바란?", content = "프로그래밍 언어", writer = "원필재"
		board.setNo(10);
		board.setTitle("자바란?");
		board.setContent("프로그래밍 언어");
		board.setWriter("원필재");
		
		System.out.println(board); // -> 데이터 업데이트
		
		// board 데이터 출력 - 항목을 하나씩 꺼내서 출력
		System.out.println("글 번호 : " + board.getNo());
		System.out.println("글 제목 : " + board.getTitle());
		System.out.println("글 내용 : " + board.getContent());
		System.out.println("작성자 : " + board.getWriter());
		
	} // end of main()

} // end of class
```
