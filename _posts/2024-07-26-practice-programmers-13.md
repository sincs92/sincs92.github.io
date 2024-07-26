---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 13일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-26 19:25:43 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. n번째 원소부터

![image-20240724204632251](/images/2024-07-24-practice-programmers-13/image-20240724204632251.png)



## 1.2. 풀이

```java
    public int[] solution(int[] num_list, int n) {
    	int newLength = num_list.length-n+1;
    	int[] answer = new int[newLength];
    	System.arraycopy(num_list, n-1, answer, 0, newLength);
    	return answer;
    }
```







## 2.1. 순서 바꾸기

![image-20240724204730897](/images/2024-07-24-practice-programmers-13/image-20240724204730897.png)

## 2.2. 풀이



```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int[] num_list, int n) {
    	List<Integer> list = new ArrayList<Integer>();
    	for(int i = 0; i < num_list.length-n; i++) {
    		list.add(num_list[i+n]);
    	}
    	for(int i = 0; i < n; i++) {
    		list.add(num_list[i]);
    	}
    	
    	int[] answer = new int[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	return answer;
    }
}
```



```java
    public int[] solution(int[] num_list, int n) {
    	int[] copy = Arrays.copyOf(num_list, num_list.length * 2);
    	System.arraycopy(num_list, 0, copy, num_list.length, num_list.length);
    	return Arrays.copyOfRange(copy, n, n + num_list.length);
    }
```





## 2.3. 참고

- [https://velog.io/@kai6666/Java-System.arraycopy-%EC%99%80Arrays.copyOf%EC%9D%98-%EC%B0%A8%EC%9D%B4-%EB%B0%B0%EC%97%B4-%EB%B3%B5%EC%82%AC](https://velog.io/@kai6666/Java-System.arraycopy-%EC%99%80Arrays.copyOf%EC%9D%98-%EC%B0%A8%EC%9D%B4-%EB%B0%B0%EC%97%B4-%EB%B3%B5%EC%82%AC)

- [https://taeil00.tistory.com/193](https://taeil00.tistory.com/193)





## 3.1. 왼쪽 오른쪽

![image-20240724204835741](/images/2024-07-24-practice-programmers-13/image-20240724204835741.png)



## 3.2. 풀이

```java
import java.util.Arrays;

class Solution {
    public String[] solution(String[] str_list) {
    	String[] answer;
    	for(int i = 0; i < str_list.length; i++) {
    		if(str_list[i].equals("r")) {
    			answer = Arrays.copyOfRange(str_list, i+1, str_list.length);
    			Arrays.copyOf(str_list, i);
    			return answer;
    		}
    		
    		if(str_list[i].equals("l")) {
    			answer = Arrays.copyOf(str_list, i);
    			return answer;
    		}
    	}
    	
    	answer = new String[0];
    	return answer;
    	
    }
}
```





## 4.1. n번째 원소까지

![image-20240724204927326](/images/2024-07-24-practice-programmers-13/image-20240724204927326.png)



## 4.2. 풀이

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] num_list, int n) {
    	return Arrays.copyOf(num_list, n);
    }
}
```



## 5.1. n개 간격의 원소들

![image-20240724205003494](/images/2024-07-24-practice-programmers-13/image-20240724205003494.png)



## 5.2. 풀이

```java
class Solution {
    public int[] solution(int[] num_list, int n) {
    	int len = num_list.length % n == 0 ? num_list.length / n : (num_list.length / n) + 1;
    	int[] answer = new int[len];
    	for(int i = 0; i < num_list.length; i++) {
    		if(i % n == 0) {
    			answer[i/n] = num_list[i];
    		}
    	}
    	return answer;
    }
}
```



## 

> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
