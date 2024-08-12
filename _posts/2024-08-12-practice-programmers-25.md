---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 25일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-12 20:20:17 +09:00
typora-root-url: ../
published: false
---







# 1. 문제



## 1.1. 정수를 나선형으로 배치하기

![image-20240812202151959](/images/2024-08-12-practice-programmers-25/image-20240812202151959.png)

## 1.2. 풀이

```java
class
```





## 2.1. 특별한 2차원 배열

![image-20240812202218249](/images/2024-08-12-practice-programmers-25/image-20240812202218249.png)





## 2.2. 풀이

```java
class Solution {
    public int solution(int[][] arr) {
    	int answer = 0;
    	boolean miss = false;
    	for(int i = 0; i < arr.length; i++) {
    		for(int j = 0; j < arr[i].length; j++) {
				if(arr[i][j] == arr[j][i]) {
					answer = 1;
				} else {
					miss = true;
				}
    		}
    	}
    	
    	if(miss) {
    		answer = 0;
    	}
    	return answer;
	}
}
```







## 3.1. 정사각형으로 만들기

![image-20240812202248643](/images/2024-08-12-practice-programmers-25/image-20240812202248643.png)



## 3.2. 풀이

```java
class
```





## 4.1. 이차원 배열 대각선 순회하기

![image-20240812200317465](/images/2024-08-09-practice-programmers-24/image-20240812200317465.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(int[][] board, int k) {
    	int sum = 0;
    	for(int i = 0; i < board.length; i++) {
    		for(int j = 0; j < board[i].length; j++) {
    			if(i + j <= k) {
    				sum += board[i][j];
    			}
    		}
    	}
    	return sum;
	}
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
