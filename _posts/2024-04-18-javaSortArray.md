---
title: "[Java] 배열 항목 반복을 위한 향상된 for 문 (배열 정렬)"
date: 2024-04-18 19:30:00 +0900
categories:
  - docs
  - java
  - algorithm
tags:
  - java
layout: single
---

# Java 알고리즘 - 배열 항목 반복을 위한 향상된 for 문 (배열 정렬)
1. 정렬
- 배열
	{ 5, 7, 2, 1, 6 }
	(1) 비교 1번째 (index - 0)
		1, 7, 5, 2, 6
	(2) 비교 2번째 (index - 1)
		1, 2, 7, 5, 6
	(3) 비교 3번째 (index - 2)
		1, 2, 5, 7, 6
	(4) 비교 4번째 (index - 3)
		1, 2, 5, 6, 7

```java
package ch05ref;

import java.util.Arrays;

public class SortArray {

	public static void main(String[] args) {

		int[] nums = { 5, 7, 2, 1, 6 };
		
		// 원본 데이터 출력 배열로 정의
		// Array는 import 해줘야 한다.
		System.out.println(Arrays.toString(nums));
		
		// 중첩 for select 소트 ( 데이터 바꿔치기 )
		// 맨 앞에 부터 차례로 작은 데이터로 정렬시키기 위해 선택한다. -> 마지막은 자동 정렬
		// i(배열 index, 초기값 = 0)가 num.length 보다 작으면 i + 1 반복해라 
		   // -> 배열에 인덱스 위치 찾고 위치 정보 증가 반복
		for (int i = 0; i < nums.length - 1; i++) {
			
			// 선택한 다음 데이터부터 마지막 데이터까지 선택 반복
			// 선택한 데이터(i) + 1 : 다음데이터(j) -> 비교하기 위해 위치 인덱스를 선택한다.
			for (int j = i + 1; j < nums.length; j++) {
				
				// 만약 첫번째 인덱스 (i) 보다 두번째 인덱스 (j)가 크면
				// 배열에 있는 값 i는 temp로 가고, j는 i로 가고, temp 는 i로 가라.
				if (nums[i] > nums[j]) {
					int temp = nums[i];
					nums[i] = nums[j];
					nums[j] = temp;
				} // end of if
			
			} // end of for j
			// 정렬 될때 마다 반복 (for i 안에서 반복)
			// System.out.println(Arrays.toString(nums));
			
		} // end of i
		
		System.out.println(Arrays.toString(nums));
	} // end of main()
} // end of class
```
