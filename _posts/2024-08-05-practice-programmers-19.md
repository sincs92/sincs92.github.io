---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 19일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-05 21:19:48 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 3개의 구분자

![image-20240805193004328](/images/2024-08-04-practice-programmers-19/image-20240805193004328.png)



## 1.2. 풀이

```java
class Solution {
    public String[] solution(String myStr) {
    	StringBuilder sb = new StringBuilder();
    	boolean lastSpace = false;
    	for(char c : myStr.toCharArray()) {
    		if(!(c=='a' || c=='b' || c=='c')) {
    			sb.append(c);
    			lastSpace = false;
    		} else {
    			if(!lastSpace) {
    				sb.append(" ");
    			}
    			lastSpace = true;
    		}
    	}
    	
    	if(sb.toString().trim().length() == 0) {
    		sb.append("EMPTY");
    	}
    	return sb.toString().trim().split(" ");
    }
}
```



정규식을 이용한 방법

```java
class Solution {
    public String[] solution(String myStr) {
    	myStr = myStr.replaceAll("[abc]+", ",");
    	myStr = myStr.charAt(0) == ',' ? myStr.substring(1) : myStr;
    	myStr = myStr.trim().length() == 0 ? "EMPTY" : myStr;
    	return myStr.split(",");
    }
}
```







## 2.1. 배열의 원소만큼 추가하기

![image-20240805195216937](/images/2024-08-04-practice-programmers-19/image-20240805195216937.png)



## 2.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr) {
    	String tempStr = "";
    	
    	for(int i = 0; i < arr.length; i++) {
    		int idx = 0;
    		while(idx < arr[i]) {
    			tempStr += arr[i];
    			tempStr += ",";
    			idx++;
    		}
    	}
    	
    	String[] strArr = tempStr.split(",");
    	int[] answer = new int[strArr.length];
    	
    	for(int i = 0; i < strArr.length; i++) {
    		answer[i] = Integer.parseInt(strArr[i]);
    	}
    	return answer;
    }
}
```





## 3.1. 빈 배열에 추가, 삭제하기

![image-20240805200714104](/images/2024-08-04-practice-programmers-19/image-20240805200714104.png)



## 3.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int[] arr, boolean[] flag) {
    	List<Integer> list = new ArrayList<Integer>();
    	for(int i = 0; i < arr.length; i++) {
    		if(flag[i] == true) {
    			int idx = 0;
    			while(idx < arr[i]) {
    				list.add(arr[i]);
    				list.add(arr[i]);
    				idx++;
    			}
			} else {
				for(int j = 0; j < arr[i]; j++) {
					list.remove(list.size() - 1);
				}
			}
    	}
    	
    	int[] answer = new int[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	
    	return answer;
    }
}
```





## 4.1. 배열 만들기 6

![image-20240805202523169](/images/2024-08-04-practice-programmers-19/image-20240805202523169.png)



## 4.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int[] arr) {
    	List<Integer> list = new ArrayList<Integer>();
    	
    	for(int i = 0; i < arr.length; i++) {
    		if(list.size() == 0) { 
    			list.add(arr[i]);
    		} else {
    			if(list.get(list.size()-1) == arr[i]) {
    				list.remove(list.size()-1);
    			} else {
    				list.add(arr[i]);
    			}
    		}
    	}
    	
    	if(list.size() == 0) {
    		list.add(-1);
    	}
    	
    	int[] stk = new int[list.size()];
    	
    	for(int i = 0; i < list.size(); i++) {
    		stk[i] = list.get(i);
    	}
    	
    	return stk;
    }
}
```





## 5.1. 무작위로 K개의 수 뽑기

![image-20240805203957477](/images/2024-08-04-practice-programmers-19/image-20240805203957477.png)



## 5.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int[] arr, int k) {
    	List<Integer> list = new ArrayList<Integer>();
    	
    	for(int i = 0; i < arr.length; i++) {
    		if(list.size() == k) {
    			break;
    		}
    		
    		if(i == 0) {
    			list.add(arr[i]);
    		} else {
    			boolean isExist =  false;
    			for(int j = 0; j < list.size(); j++) {
    				if(arr[i] == list.get(j)) {
    					isExist = true;
    				}
    			}
    			if(!isExist) {
    				list.add(arr[i]);
    			}
    		}
    	}
    	
    	if(list.size() < k) {
    		while(list.size() < k) {
    			list.add(-1);
    		}
    	}
    	
    	int[] answer = new int[list.size()];
    	
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	
    	return answer;
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
