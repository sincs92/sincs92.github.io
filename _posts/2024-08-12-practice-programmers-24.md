---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 24일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-12 20:20:17 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 커피 심부름

![image-20240812172853369](/images/2024-08-09-practice-programmers-24/image-20240812172853369.png)

![image-20240812172912060](/images/2024-08-09-practice-programmers-24/image-20240812172912060.png)

## 1.2. 풀이

```java
class Solution {
    public int solution(String[] order) {
    	int amePrice = 4500;
    	int cafePrice = 5000;
    	int sum = 0;
    	
    	for(String s : order) {
    		if(s.contains("americano") || s.equals("anything")) {
    			sum += amePrice;
    		} else if (s.contains("cafelatte")) {
    			sum += cafePrice;
    		}
    	}
    	
		return sum;
	}
}
```





## 2.1. 그림 확대

![image-20240812173949326](/images/2024-08-09-practice-programmers-24/image-20240812173949326.png)





## 2.2. 풀이

```java
import java.util.List;
import java.util.ArrayList;

class Solution {
    public String[] solution(String[] picture, int k) {
    	List<String> list = new ArrayList<String>();
    	
    	for(int i = 0; i < picture.length; i++) {
    		String temp = "";
    		for(char c : picture[i].toCharArray()) {
    			for(int j = 1; j <= k; j++) {
    				temp += c;
    			}
    		}
    		
    		for(int j = 1; j <= k; j++) {
    			list.add(temp);
    		}
    	}
    	
    	String[] answer = new String[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
		return answer;
	}
}
```







## 3.1. 조건에 맞게 수열 변환하기 3

![image-20240812195722690](/images/2024-08-09-practice-programmers-24/image-20240812195722690.png)



## 3.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr, int k) {
    	for(int i = 0; i < arr.length; i++) {
    	    if(k % 2 > 0) {
    	        arr[i] *= k;
    	    } else {
    	        arr[i] += k;
    	    }
    	}
		return arr;
	}
}
```





## 4.1. I로 만들기

![image-20240812200317465](/images/2024-08-09-practice-programmers-24/image-20240812200317465.png)



## 4.2. 풀이

```java
class Solution {
    public String solution(String myString) {
		StringBuilder sb = new StringBuilder();
    	for(char c : myString.toCharArray()) {
    		if(c < 108) {
    			sb.append("l");
    		} else {
    			sb.append(c);
    		}
    	}
    	return sb.toString();
	}
}
```





## 5.1. 특별한 2차원

![image-20240812200908872](/images/2024-08-09-practice-programmers-24/image-20240812200908872.png)



## 5.2. 풀이

```java
class Solution {
    public int[][] solution(int n) {
    	int[][] answer = new int[n][n];
    	for(int i = 0; i < answer.length; i++) {
    		answer[i][i] = 1;
    	}
    	return answer;
	}
}
```



> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
