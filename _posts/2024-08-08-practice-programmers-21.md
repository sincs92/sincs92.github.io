---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 21일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-08 19:48:53 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 뒤에서 5등 위로

![image-20240808184544102](/images/2024-08-07-practice-programmers-21/image-20240808184544102.png)



## 1.2. 풀이

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] num_list) {
    	Arrays.sort(num_list);
    	return Arrays.copyOfRange(num_list, 5, num_list.length);
    }
}
```



## 2.1. 전국 대회 선발 고사

![image-20240808185306507](/images/2024-08-07-practice-programmers-21/image-20240808185306507.png)





## 2.2. 풀이

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int solution(int[] rank, boolean[] attendance) {
    	int a = 0; int b = 0; int c = 0;
    	List<Integer> list = new ArrayList<Integer>();
    	
    	// attendance에 따라 불참자를 제외한 List 구하기
    	for(int i = 0; i < rank.length; i++) {
    		if(attendance[i] != false) {
    			list.add(rank[i]);
    		}
    	}
    	
    	// List를 배열로 변환
    	int[] listArr = new int[list.size()];
    	
    	for(int i = 0; i < list.size(); i++) {
    		listArr[i] = list.get(i);
    	}
    	
    	// 배열을 오름차순 정렬하고 Top3를 뽑은 배열 생성 (참석자 중 가장 높은 순위 3개)
    	Arrays.sort(listArr);
    	
    	int[] topThreeRanks = Arrays.copyOf(listArr, 3)  ;
    	
    	// 해당 순위를 거둔 사람을 원본 배열에서 찾음
    	for(int i = 0; i < rank.length; i++) {
    		if(rank[i] == topThreeRanks[0]) a = i;
    		if(rank[i] == topThreeRanks[1]) b = i;
    		if(rank[i] == topThreeRanks[2]) c = i;
    	}
    	
    	// 찾은 인덱스를 가지고 연산 후 반환
    	return 10000 * a + 100 * b + c;
    }
}
```





## 3.1. 정수 부분

![image-20240808194135513](/images/2024-08-07-practice-programmers-21/image-20240808194135513.png)



## 3.2. 풀이

```java
class Solution {
    public int solution(double flo) {
		return (int)flo;
	}
}
```





## 4.1. 문자열 정수의 합

![image-20240808194411725](/images/2024-08-07-practice-programmers-21/image-20240808194411725.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(String num_str) {
    	String[] strArr = num_str.split("");
    	int sum = 0;
    	for(String s : strArr) {
    		sum += Integer.parseInt(s);
    	}
		return sum;
	}
}
```





## 5.1. 문자열을 정수로 변환하기

![image-20240808194740704](/images/2024-08-07-practice-programmers-21/image-20240808194740704.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(String n_str) {
		return Integer.parseInt(n_str);
	}
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
