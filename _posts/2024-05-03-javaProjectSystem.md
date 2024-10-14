---
title: "[Java] 프로젝트 시스템 구조, JDBC"
date: 2024-05-03 19:20:00 +0900
categories:
  - docs
  - java
tags:
  - java
  - jdbc
layout: single
---
## Java 프로젝트 구조
- 모든 프로젝트는 main이 한 개

![Java Project System](/assets/images/javaProjectSystem.png)

## JDBC

### JDBC란?
- JDBC(Java Database Connectivity)는 Java에서 데이터베이스와 상호작용하기 위한 표준 API이다. JDBC를 사용하면 Java 애플리케이션이 다양한 데이터베이스에 연결하고, 데이터를 쿼리하거나 업데이트하는 작업을 수행할 수 있다. 이를 통해 데이터베이스에 독립적인 코드 작성을 가능하게 하며, 다양한 데이터베이스 관리 시스템(DBMS)을 지원한다.

### JDBC의 주요 개념
1. JDBC 드라이버
    - JDBC는 데이터베이스와의 통신을 위해 특정 데이터베이스에 맞는 JDBC 드라이버가 필요하다. 일반적으로 데이터베이스 벤더가 제공하며, Java 프로그램이 데이터베이스와 연결하고 명령을 수행할 수 있도록 한다.
    - JDBC 드라이버 유형:
        - Type-1: JDBC-ODBC 브리지 드라이버
        - Type-2: 네이티브 API 드라이버
        - Type-3: 네트워크 프로토콜 드라이버
        - Type-4: 네이티브 프로토콜 드라이버 (일반적으로 가장 많이 사용됨)

2. JDBC 연결 과정
    - 1단계: 드라이버 로드 – Class.forName()을 통해 드라이버 클래스를 로드한다.
    - 2단계: 연결 생성 – DriverManager.getConnection() 메서드를 통해 데이터베이스에 연결한다.
    - 3단계: SQL 문 실행 – Statement, PreparedStatement, CallableStatement 등을 사용해 SQL 쿼리를 실행한다.
    - 4단계: 결과 처리 – ResultSet 객체를 통해 쿼리 결과를 처리한다.
    - 5단계: 연결 종료 – 사용이 끝난 후 데이터베이스 연결을 닫는다.

### 일반 게시판 DAO 예시

### BoardListDAO
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class BoardListDAO {
	
	// 맨 처음 처리되는 main()
	public static void main(String[] args) {
		System.out.println("BoardListDAO.main() - 시작");
		
		// JDBC에 필요한 객체 선언
		// connection -> import 해야 함.
		Connection con = null; // 연결 객체 - 서버, 아이디, 비밀번호
		PreparedStatement pstmt = null; // 실행 객체 - sql과 데이터
		ResultSet rs = null; // 데이터를 가져왔을 때 결과 저장 객체 - select
		
		try {
			// 1. 드라이버 확인과 필요한 객체 로딩(static 객체 자동으로 올라가게 해야 한다.)
			// oracle.jdbc.OracleDriver와 동일한 클래스
			// 프로젝트 시작에서 딱 한번만 확인하면 된다.
			Class.forName("oracle.jdbc.driver.OracleDriver"); // 클래스 이름 확인 Class.forname
			System.out.println("1. 드라이버 확인 완료");
			
			// 2. 접속 가능한지 확인 - 연결 확인
			con = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe", "----", "----");
			System.out.println("2. 오라클 연결 성공");
			
			// 3. 실행 쿼리
			String sql = "select no, title, writer, writeDate, hit "
					+ " from board "
					+ " order by no desc";
			System.out.println("3. sql - " + sql);
			
			// 4. 실행 객체에 sql 넣기와 데이터 세팅
			pstmt = con.prepareStatement(sql);
			System.out.println("4. 실행 객체 생성 완료");
			
			// 5. 실행 해서 데이터 가져오기 - select
			rs = pstmt.executeQuery();
			System.out.println("5. 실행 성공 - 데이터 가져오기");
			
			// 6. 데이터 표시 & 담기 - BoardVO에 답는다. 컬렉션에 VO를 담는다. (ArrayList)
			// 지금은 바로 출력해 보자.
			if(rs != null) {
				// rs.next() -> 다음 데이터로 포인터를 이동시켜 준다. 다음 데이터가 없으면 false를 리턴해 준다. while문 빠져 나감.
				System.out.println("번호 / 제목 / 작성자 / 작성일 / 조회수");
				while(rs.next()) { // 있는 데이터 모두 처리
					System.out.print(rs.getLong("no"));
					System.out.print(" / " + rs.getString("title"));
					System.out.print(" / " + rs.getString("writer"));
					System.out.print(" / " + rs.getString("writeDate"));
					System.out.println(" / " + rs.getLong("hit"));
				} // end of while
			} // end of if
			System.out.println("6. 데이터 표시 성공");
			
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
			System.out.println("1. 드라이버 확인 실패");
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
			System.out.println("2. 오라클 연결 실패 또는 4. 실행 객체 생성 실패");
			System.out.println(" 또는 5. 실행 오류");
		} finally {
				try {
					// 7. 닫기
					if(con != null)	con.close();
					if(pstmt != null)	pstmt.close();
					if(rs != null)	rs.close();
					System.out.println("7. 객체 닫기 성공");
				} catch (SQLException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
					System.out.println("7. 객체 닫기 오류");
				}
		} // end of try ~ catch
		
		System.out.println("BoardListDAO.main() - 끝");
		
	} // end of main()
} // end of class
```

### BoardViewDAO
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

public class BoardViewDAO {
	public static void main(String[] args) {
		
		// 필요한 객체 선언
		Connection con = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		// 오라클 접속 정보 - 드라이버, sever url, ID, PW
		String driver = "oracle.jdbc.driver.OracleDriver"; // 
		String url = "jdbc:oracle:thin:@localhost:1521:xe";
		String id = "java";
		String pw = "java";
		
		// 데이터 정보
		long no = 128;
		
		try {
			// 1. 드라이버 확인과 객체 로딩
			Class.forName(driver);
			System.out.println("1. 드라이버 확인 완료");
			
			// 2. 접속 가능한지 확인 - 연결 확인
			con = DriverManager.getConnection(url, "java", "java");
			System.out.println("2. 드라이버 연결 완료");
			
			// 3. 실행 쿼리
			String sql = "select no, title, content, writer, writeDate, hit "
					+ " from board "
					+ " where no = ?";
			System.out.println("3. 실행 쿼리 : " + sql);
			
			// 4. 실행 객체에 sql 넣기 & 데이터 세팅
			pstmt = con.prepareStatement(sql);
			pstmt.setLong(1, no);
			System.out.println("4. 실행 객체 생성 완료");
			
			// 5. 실행 해서 데이터 가져오기 - select
			rs = pstmt.executeQuery();
			System.out.println("5. 실행 성공 - 데이터 가져오기");
			
			// 6. 데이터 표시 & 담기
			if (rs != null && rs.next()) {
				System.out.println("번호 : " + rs.getLong("no"));
				System.out.println("제목 : " + rs.getString("title"));
				System.out.println("글 내용 : " + rs.getString("content"));
				System.out.println("작성자 : " + rs.getString("writer"));
				System.out.println("작성일 : " + rs.getString("writeDate"));
				System.out.println("조회수 : " + rs.getLong("hit"));
				System.out.println("6. 데이터 가져오기 성공");
			}
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			System.out.println("오류");
		} finally {
			try {
				// 7. 닫기
				if(con != null) con.close();
				if(pstmt != null) pstmt.close();
				if(rs != null) rs.close();
				System.out.println("7. 닫기 성공");
			} catch (Exception e) {
				// TODO: handle exception
				e.printStackTrace();
			}
		}
	} // end of main()
} // end of class
```