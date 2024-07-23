---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 11일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-23 19:41:09 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 문자 개수 세기

![image-20240723184137929](/images/2024-07-23-practice-programmers-11/image-20240723184137929.png)



## 1.2. 풀이

```java
class Solution {
    public int[] solution(String my_string) {
    	int[] arr = new int[52];
    	// 대문자는 65 ~ 90, 소문자는 97 ~ 122
    	// 배열에서 대문자 인덱스는 0 ~ 25, 소문자는 26 ~51
    	for(int i = 0; i < my_string.length(); i++) {
    		char ab = my_string.charAt(i);
    		if(Character.isUpperCase(ab)) {	// 대문자라면..
    			arr[ab-65] += 1;
    		} else {
    			arr[ab-71] += 1;
    		}
    	}
    	return arr;
    }
}
```







## 2.1. 배열 만들기

![image-20240723184632247](/images/2024-07-23-practice-programmers-11/image-20240723184632247.png)

## 2.2. 풀이



```java
class Solution {
    public int[] solution(int n, int k) {
    	int[] arr = new int[n/k];
    	for(int i = 0; i < arr.length; i++) {
    		arr[i] = (i+1) * k;
    	}
		return arr;
	}
}
```





## 3.1. 글자 지우기

![image-20240723185137977](/images/2024-07-23-practice-programmers-11/image-20240723185137977.png)



## 3.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public String solution(String my_string, int[] indices) {
    	StringBuilder sb = new StringBuilder();
    	
        // 배열을 리스트로 변환
    	List<Integer> indicesList = new ArrayList<>();
    	for(int i = 0; i < indices.length; i++) {
    		indicesList.add(indices[i]);
    	}
    	
        // contains 메소드를 이용하여 인덱스 i가 지워야하는 인덱스 배열(indicesList)에 포함되어있는지 판별
    	for(int i = 0; i < my_string.length(); i++) {
    		if(!indicesList.contains(i)) {	// indicesList에 포함되어 있지 않다면 문자열을 더함
    			sb.append(my_string.charAt(i));
    		}
    	}
		return sb.toString();
	}
}
```





## 4.1. 카운트 다운

![image-20240723191659533](/images/2024-07-23-practice-programmers-11/image-20240723191659533.png)



## 4.2. 풀이

```java
class Solution {
    public int[] solution(int start_num, int end_num) {
    	int[] answer = new int[start_num-end_num+1];
    	for(int i = 0; i < answer.length; i++) {
    		answer[i] = start_num-i;
    	}
    	return answer;
	}
}
```



## 5.1. 가까운 1 찾기

![image-20240723192257900](/images/2024-07-23-practice-programmers-11/image-20240723192257900.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(int[] arr, int idx) {
    	int answer = -1;
    	for(int i = 0; i < arr.length; i++) {
    		if(i >= idx && arr[i] == 1) {
    			answer = i;
    			return answer;
    		}
    	}
    	return answer;
	}
}
```



##  

> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
