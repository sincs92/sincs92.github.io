---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 14일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-26 20:29:09 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 홀수 vs 짝수

![image-20240726192833902](/images/2024-07-26-practice-programmers-14/image-20240726192833902.png)



## 1.2. 풀이

```java
class Solution {
    public int solution(int[] num_list) {
    	int oSum = 0;
    	int eSum = 0;
    	for(int i = 0; i < num_list.length; i++) {
    		int su = num_list[i];
    		if(i % 2 == 0) eSum+=su;
    		if(i % 2 != 0) oSum+=su;
    	}
    	return oSum > eSum ? oSum : eSum;
    }
}
```







## 2.1. 5명씩

![image-20240726194341330](/images/2024-07-26-practice-programmers-14/image-20240726194341330.png)

## 2.2. 풀이



```java
class Solution {
    public String[] solution(String[] names) {
    	int len = names.length % 5 == 0 ? (names.length) / 5 : (names.length / 5) + 1;
    	String[] answer = new String[len];
    	int idx = 0;
    	for(int i = 0; i < answer.length; i++) {
    		answer[idx++] = names[i * 5];
    	}
    	return answer;
    }
}
```





## 3.1. 할 일 목록

![image-20240726195952737](/images/2024-07-26-practice-programmers-14/image-20240726195952737.png)



## 3.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public String[] solution(String[] todo_list, boolean[] finished) {
    	List<String> list = new ArrayList<String>();
    	for(int i = 0; i < todo_list.length; i++) {
    		if(finished[i] == false) list.add(todo_list[i]);
    	}
    	
    	String[] answer = new String[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	
    	return answer;
    }
}
```



풀고나니 다른 사람들의 풀이 중 더 간편한 방법이 있어서 참고해 다시 풀어보았다.



```java
    public String[] solution(String[] todo_list, boolean[] finished) {
    	String str = "";
    	for(int i = 0; i < todo_list.length; i++) {
    		str = finished[i] == false ? str += todo_list[i] + "," : str;
    	}
    	return str.split(",");
    }
```







## 4.1. n보다 커질 때까지 더하기

![image-20240726201506271](/images/2024-07-26-practice-programmers-14/image-20240726201506271.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(int[] numbers, int n) {
    	int answer = 0;
    	for(int i = 0; i < numbers.length; i++) {
    		if(answer > n) break;
    		answer += numbers[i];
    	}
    	return answer;
    }
}
```



## 5.1. 수열과 구간 쿼리 1

![image-20240726202022467](/images/2024-07-26-practice-programmers-14/image-20240726202022467.png)



## 5.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
    	for(int i = 0; i < queries.length; i++) {
	    	for(int j = 0; j < arr.length; j++) {
    			if(j >= queries[i][0] && j <= queries[i][1]) {
    				arr[j]++;
    			}
	    	}
    	}
    	return arr;
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
