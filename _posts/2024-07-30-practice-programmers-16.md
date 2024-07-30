---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 16일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-30 18:45:31 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 대문자로 바꾸기

![image-20240730180523762](/images/2024-07-30-practice-programmers-16/image-20240730180523762.png)



## 1.2. 풀이

```java
class Solution {
    public String solution(String myString) {
    	return myString.toUpperCase();
    }
}
```







## 2.1. 소문자로 바꾸기

![image-20240730180712220](/images/2024-07-30-practice-programmers-16/image-20240730180712220.png)



## 2.2. 풀이

```java
class Solution {
    public String solution(String myString) {
    	return myString.toLowerCase();
    }
}
```





## 3.1. 배열에서 문자열 대소문자 변환하기

![image-20240730180851371](/images/2024-07-30-practice-programmers-16/image-20240730180851371.png)



## 3.2. 풀이

```java
class Solution {
    public String[] solution(String[] strArr) {
    	for(int i = 0; i < strArr.length; i++) {
    		if(i % 2 == 0) {
    			strArr[i] = strArr[i].toLowerCase();
    		} else if(i % 2 > 0) {
    			strArr[i] = strArr[i].toUpperCase();
    		}
    	}
    	return strArr;
    }
}
```





## 4.1. A 강조하기

![image-20240730181800034](/images/2024-07-30-practice-programmers-16/image-20240730181800034.png)



## 4.2. 풀이

```java
class Solution {
    public String solution(String myString) {
    	StringBuilder sb = new StringBuilder();
    	String[] strArr = myString.split("");
    	
    	for(int i = 0; i < strArr.length; i++) {
    		if(strArr[i].equals("a") || strArr[i].equals("A")) {
    			strArr[i] = "A";
    		} else {
    			strArr[i] = strArr[i].toLowerCase();
    		}
    	}
    	
    	for(int i = 0; i < strArr.length; i++) {
    		sb.append(strArr[i]);
    	}
    	
    	return sb.toString();
    }
}
```



```java
class Solution {
	public String solution(String myString) {
    	myString = myString.toLowerCase();
    	myString = myString.replace('a', 'A');
    	return myString;
    }
}
```



이런 간단한 방법을 먼저 떠올리지 못한 것을 반성하게 된다..



## 5.1. 특정한 문자를 대문자로 바꾸기

![image-20240730184157085](/images/2024-07-30-practice-programmers-16/image-20240730184157085.png)



## 5.2. 풀이

```java
class Solution {
    public String solution(String my_string, String alp) {
    	return my_string.replace(alp, alp.toUpperCase());
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
