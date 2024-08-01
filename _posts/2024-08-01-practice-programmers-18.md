---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 18일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-01 22:20:32 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. x 사이의 개수

![image-20240801210730062](/images/2024-08-01-practice-programmers-18/image-20240801210730062.png)



## 1.2. 풀이

```java
class Solution {
    public int[] solution(String myString) {
    	String[] strArr = myString.split("x", -1);
    	int[] answer = new int[strArr.length];
    	for(int i = 0; i < answer.length; i++) {
    		answer[i] = strArr[i].length();
    	}
    	return answer;
    }
}
```



처음에

```java
String[] strArr = myString.split("x");
```

이렇게 x 문자열로 나누도록 했지만 값을 찍어보면 기대결과인 [1, 2, 1, 0, 1, 0]이 아니라 [1, 2, 1, 0, 1]이 나왔다. 이는 마지막의 빈 문자열은 포함하지 않는 split메소드의 특징으로 limit파라미터를 추가하여 되면 정상적으로 결과값이 나오게되었다.

(참고 : [https://blog.naver.com/0neslife/220816476627](https://blog.naver.com/0neslife/220816476627))





## 2.1. 문자열 잘라서 정렬하기

![image-20240801213531537](/images/2024-08-01-practice-programmers-18/image-20240801213531537.png)



## 2.2. 풀이

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public String[] solution(String myString) {
    	List<String> list = new ArrayList<String>();
    	String[] strArr = myString.split("x");
    	
    	for(int i = 0; i < strArr.length; i++) {
    		if(!strArr[i].equals("")) {
    			list.add(strArr[i]);
    		}
    	}
    	
    	String[] answer = new String[list.size()];
    	
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	
    	Arrays.sort(answer);
    	
    	return answer;
    }
}
```





## 3.1. 간단한 식 계산하기

![image-20240801214938663](/images/2024-08-01-practice-programmers-18/image-20240801214938663.png)



## 3.2. 풀이

```java
class Solution {
    public int solution(String binomial) {
    	String[] strArr = binomial.split(" ");
    	int a = Integer.parseInt(strArr[0]);
    	int b = Integer.parseInt(strArr[2]);
    	String op = strArr[1];
    	int res = 0;
    	
    	switch(op) {
    		case "+":
    			res = a + b;
    			break;
    			
    		case "-":
    			res = a - b;
    			break;
    			
    		case "*":
    			res = a * b;
    			break;
    	}
    	
    	return res;
    }
}
```





## 4.1. 문자열 찾기

![image-20240801215605871](/images/2024-08-01-practice-programmers-18/image-20240801215605871.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(String myString, String pat) {
    	char[] charArr = myString.toCharArray();
    	StringBuilder sb = new StringBuilder();
    	
    	for(char c : charArr) {
    		if(c == 'A') {
    			c = 'B';
    		} else if(c == 'B') {
    			c = 'A';
    		}
    		
    		sb.append(c);
    	}
    	
    	if(sb.toString().contains(pat)) {
    		return 1;
    	} else {
    		return 0;
    	}
    }
}
```





## 5.1. rny_string

![image-20240801221325580](/images/2024-08-01-practice-programmers-18/image-20240801221325580.png)



## 5.2. 풀이

```java
class Solution {
    public String solution(String rny_string) {
    	char[] charArr = rny_string.toCharArray();
    	StringBuilder sb = new StringBuilder();
    	
    	for(char c : charArr) {
    		if(c == 'm') {
    			sb.append("rn");
    		} else {
    			sb.append(c);
    		}
    	}
    	return sb.toString();
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
