---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 17일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-31 21:11:31 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 특정 문자열로 끝나는 가장 긴 부분 문자열 찾기

![image-20240731171439950](/images/2024-07-31-practice-programmers-17/image-20240731171439950.png)



## 1.2. 풀이

```java
class Solution {
    public String solution(String myString, String pat) {
    	return myString.substring(0, myString.lastIndexOf(pat) + pat.length());
    }
}
```







## 2.1. 문자열이 몇 번 등장하는지 세기

![image-20240731173055466](/images/2024-07-31-practice-programmers-17/image-20240731173055466.png)



## 2.2. 풀이

```java
class Solution {
    public int solution(String myString, String pat) {
    	int cnt = 0;
    	int idx = 0;
    	String temp = myString;
    	while(idx < temp.length()) {
    		temp = temp.substring(idx, temp.length());
    		if(temp.indexOf(pat) > -1) {
    			cnt++;
    			idx = temp.indexOf(pat)+1;
    		} else {
    			idx++;
    		}
    	};
    	return cnt;
    }
}
```





## 3.1. ad제거하기

![image-20240731190456861](/images/2024-07-31-practice-programmers-17/image-20240731190456861.png)



## 3.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public String[] solution(String[] strArr) {
    	List<String> list = new ArrayList<String>();
    	for(int i = 0; i < strArr.length; i++) {
    		if(strArr[i].indexOf("ad") == -1) {
    			list.add(strArr[i]);
    		}
    	}
    	
    	String[] resArr = new String[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		resArr[i] = list.get(i);
    	}
    	return resArr;
    }
}
```





## 4.1. 공백으로 구분하기 1

![image-20240731201547975](/images/2024-07-31-practice-programmers-17/image-20240731201547975.png)



## 4.2. 풀이

```java
class Solution {
    public String[] solution(String my_string) {
    	return my_string.split(" ");
    }
}
```





## 5.1. 공백으로 구분하기 2

![image-20240731203544018](/images/2024-07-31-practice-programmers-17/image-20240731203544018.png)



## 5.2. 풀이

```java
class Solution {
    public String[] solution(String my_string) {
    	StringBuilder sb = new StringBuilder();
    	char[] charArr = my_string.toCharArray();
    	boolean lastSpace = false;
    	for(char c : charArr) {
    		if(c == ' ') {
    			if(!lastSpace) {
    				sb.append(c);
    			}
    			lastSpace = true;
    		} else {
    			sb.append(c);
    			lastSpace = false;
    		}
    	}
    	return sb.toString().trim().split(" ");
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
