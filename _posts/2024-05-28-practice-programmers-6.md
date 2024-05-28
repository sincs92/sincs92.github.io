---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 6일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-28 18:04:00 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 마지막 두 원소

![image-20240528180523007](/images/2024-05-28-practice-programmers-6/image-20240528180523007.png)

![image-20240528180538603](/images/2024-05-28-practice-programmers-6/image-20240528180538603.png)

## 1.2. 풀이

```java
class Solution {
    public int[] solution(int[] num_list) {
        int[] answer = new int[num_list.length+1];
        int lastElem = num_list[num_list.length-1];
        int exLastElem = num_list[num_list.length-2];
        int nextElem = lastElem > exLastElem ? lastElem - exLastElem : lastElem + lastElem;
        for(int i = 0; i < num_list.length; i++) {
            answer[i] = num_list[i];
        }
        answer[answer.length-1] = nextElem;
        return answer;
    }
}
```





## 2.1. 수 조작하기 1

![image-20240528181641838](/images/2024-05-28-practice-programmers-6/image-20240528181641838.png)

![image-20240528181700459](/images/2024-05-28-practice-programmers-6/image-20240528181700459.png)

## 2.2. 풀이

```java
class Solution {
    public int solution(int n, String control) {
        int answer = n;
        char[] controlCharArr = control.toCharArray();
        for(int i = 0; i < controlCharArr.length; i++) {
            switch(controlCharArr[i]) {
                case 'w': 
                    answer += 1; 
                    break;
                case 's': 
                    answer -= 1; 
                    break;
                case 'd': 
                    answer += 10; 
                    break;
                case 'a': 
                    answer -= 10; 
                    break;
            }
        }
        return answer;
    }
}
```



## 3.1. 수 조작하기 2

![image-20240528183313486](/images/2024-05-28-practice-programmers-6/image-20240528183313486.png)

![image-20240528183346220](/images/2024-05-28-practice-programmers-6/image-20240528183346220.png)

## 3.2. 풀이

```java
class Solution {
    public String solution(int[] numLog) {
        String answer = "";
        for(int i = 0; i < numLog.length - 1; i++) {
            switch(numLog[i+1] - numLog[i]) {
                case 1:
                    answer += "w";
                    break;
                case -1:
                    answer += "s";
                    break;
                case 10:
                    answer += "d";
                    break;
                case -10:
                    answer += "a";
                    break;
            }
        }
        return answer;
    }
}
```



## 4.1. 수열과 구간 쿼리 3

![image-20240528184333252](/images/2024-05-28-practice-programmers-6/image-20240528184333252.png)

![image-20240528184346811](/images/2024-05-28-practice-programmers-6/image-20240528184346811.png)

## 4.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        for(int i = 0; i < queries.length; i++) {
            int[] query = queries[i];
            int temp = 0;
            temp = arr[query[0]];
            arr[query[0]] = arr[query[1]];
            arr[query[1]] = temp;
        }
        return arr;
    }
}
```





## 5.1. 수열과 구간 쿼리 2

![image-20240528202211373](/images/2024-05-28-practice-programmers-6/image-20240528202211373.png)

![image-20240528202221286](/images/2024-05-28-practice-programmers-6/image-20240528202221286.png)

## 5.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        int[] answer = new int[queries.length];
        for(int i = 0; i < queries.length; i++) {
        	int temp = -1;
            for(int j = queries[i][0]; j <= queries[i][1]; j++) {
            	if(arr[j] > queries[i][2]) {
            		if(temp == -1 || arr[j] < temp) {
            			temp = arr[j];
            		}
            	}
            }
            answer[i] = temp;
        }
        return answer;
    }
}
```



```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        int[] answer = new int[queries.length];
        Arrays.fill(answer, -1);
        for(int i = 0; i < queries.length; i++) {
            for(int j = queries[i][0]; j <= queries[i][1]; j++) {
            	if(arr[j] > queries[i][2]) {
            		answer[i] = answer[i] == -1 ? arr[j] : Math.min(answer[i], arr[j]);
            	}
            }
        }
        return answer;
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
