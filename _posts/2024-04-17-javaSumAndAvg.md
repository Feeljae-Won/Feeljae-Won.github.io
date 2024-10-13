---
title: "[Java] for문을 사용한 합계와 평균"
date: 2024-04-17 19:20:00 +0900
categories:
  - docs
  - java
  - algorithm
tags:
  - java
layout: single
---

# Java 알고리즘 - for문을 사용한 합계와 평균

```java
package ch04condition;

/**
 *  - 85, 70, 95, 100의 데이터의 합계와 평균을 구하는 프로그램 작성
 *  	1) index와 length를 사용하는 방법
 *  	2) 향상된 for(=foreach)
 *  	- 배열 사용
 *  	- 변수 - int sum, avg 
 */
public class PrecticeSumAndAvg {
	public static void main(String[] args) {
			
		// 필재 풀이
		int [] scores = {85, 70, 95, 100};
		int sum = 0;
		
		for (int i : scores) {
			System.out.print(i + " "); // 점수 나열
			sum += i; 
		}
		
		int avg = sum/scores.length;
		System.out.println();
		System.out.println("점수 합계는? " + sum);
		System.out.println("점수 평균은? " + avg);
	
		System.out.println("----- 필재 풀이 -----");
		System.out.println("");
		
		// ------------------------- 풀이
		// 데이터
		int[] data1 = {85,70,95,100};
		
		System.out.println("for length 사용");
		// 합계와 평균 - 초기화
		int sum1 = 0;
		int avg1 = 0;
		
		// 합계 - 위에 숫자를 더해서 sum에 넣는다. 데이터 개수 만큼 반복 처리
		for(int i = 0; i < data1.length; i++) sum1 += data1[i];
		
		avg = sum / data1.length; // 평균 = 점수들의 합계 / 갯수
		
		// 결과 출력
		System.out.println("합계 : " + sum);
		System.out.println("평균 : " + avg);
		
		
		System.out.println("foreach문 사용");
		sum1 = 0;
		avg1 = 0;
		
		// 합계 - 위에 숫자를 더해서 sum에 넣는다. 데이터 개수 만큼 반복 처리
		for(int i : data1) sum1 += i;
		
		avg = sum / data1.length; // 평균 = 점수들의 합계 / 갯수
		System.out.println("합계 : " + sum);
		System.out.println("평균 : " + avg);
		
		System.out.println("----- 강사 풀이 -----");
		System.out.println("");	
	}
}
```
