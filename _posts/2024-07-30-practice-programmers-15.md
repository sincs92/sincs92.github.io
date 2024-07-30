---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 15일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-30 18:04:20 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 조건에 맞게 수열 변환하기 1

![image-20240730172434077](/images/2024-07-30-practice-programmers-15/image-20240730172434077.png)



## 1.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr) {
    	for(int i = 0; i < arr.length; i++) {
    		if(arr[i] >= 50 && arr[i] % 2 == 0) {
    			arr[i] /= 2; 
    		} else if(arr[i] < 50 && arr[i] % 2 != 0) {
    			arr[i] *= 2; 
    		} else {
    			arr[i] = arr[i];
    		}
    	}
    	return arr;
    }
}
```







## 2.1. 조건에 맞게 수열 변환하기 2

![image-20240730172924984](/images/2024-07-30-practice-programmers-15/image-20240730172924984.png)



## 2.2. 풀이

```java
class Solution {
    public int solution(int[] arr) {
    	int idx = 0;
    	while(true) {
    		int changed = 0;
    		for(int i = 0; i < arr.length; i++) {
    			if(arr[i] >= 50 && arr[i] % 2 == 0) {
    				arr[i] /= 2; 
    				changed++;
    			} else if(arr[i] < 50 && arr[i] % 2 != 0) {
    				arr[i] = arr[i] * 2 + 1;
    				changed++;
    			} 
    		}
    		if(changed == 0) {
    			break;
    		}
    		idx++;
    	}
    	return idx;
    }
}
```





## 3.1. 1로 만들기

![image-20240730174254024](/images/2024-07-30-practice-programmers-15/image-20240730174254024.png)



## 3.2. 풀이

```java
class Solution {
    public int solution(int[] arr) {
    	int cnt = 0;
    	for(int i = 0; i < arr.length; i++) {
    		while(true) {
    			if(arr[i] == 1) {
    				break;
    			}
    			if(arr[i] % 2 == 0) {
    				arr[i] /= 2;
    				cnt++;
    			} else {
    				arr[i] -= 1;
    				arr[i] /= 2;
    				cnt++;
    			}
    		}
    	}
    	return cnt;
    }
}
```





## 4.1. 길이에 따른 연산

![image-20240730175250010](/images/2024-07-30-practice-programmers-15/image-20240730175250010.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(int[] arr) {
    	int answer = 0;
    	if(arr.length >= 11) {
    		for(int i = 0; i < arr.length; i++) {
    			answer += arr[i];
    		}
    	} else {
    		answer += 1;
    		for(int i = 0; i < arr.length; i++) {
    			answer *= arr[i];
    		}
    	}
    	return answer;
    }
}
```



## 5.1. 수열과 구간 쿼리 1

![image-20240730175723609](/images/2024-07-30-practice-programmers-15/image-20240730175723609.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(String myString, String pat) {
    	return myString.toLowerCase().contains(pat.toLowerCase()) ? 1 : 0;
	}
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
