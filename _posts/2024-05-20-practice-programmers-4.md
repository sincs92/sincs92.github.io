---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 4일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-20 17:53:00 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. n의 배수

![image-20240516202336959](/images/2024-05-16-practice-programmers-3/image-20240516202336959.png)

## 1.2. 풀이

```java
class Solution {
    public int solution(int num, int n) {
        int answer = 0;
        answer = num % n == 0 ? 1 : 0;
        return answer;
    }
}
```





## 2.1. 공배수

![image-20240516202755068](/images/2024-05-16-practice-programmers-3/image-20240516202755068.png)

## 2.2. 풀이

```java
class Solution {
    public int solution(int number, int n, int m) {
        int answer = number % n == 0 && number % m == 0 ? 1 : 0;
        return answer;
    }
}
```





## 3.1. 홀짝에 따라 다른 값 반환하기

![image-20240516203137986](/images/2024-05-16-practice-programmers-3/image-20240516203137986.png)



## 3.2. 풀이

```java
class Solution {
    public int solution(int n) {
        int answer = 0; 
        if(n % 2 != 0) {    // 홀수!
            answer = sum(n);
        } else {            // 짝수!
            answer = sqSum(n);
        }
        return answer;
    }
    
    public int sum (int n) {
        int sum = 0;
        for(int i = 1; i <= n; i++) {
            if(i % 2 != 0) {
                sum += i;
            }
        }
        return sum;
    }
    
    public int sqSum (int n) {
        int sqSum = 0;
        for(int i = 1; i <= n; i++) {
            if(i % 2 == 0) {
                sqSum += i*i;
            }
        }
        return sqSum;
    }
}
```



```java
    public int solution(int n) {
        int answer = 0; 
        for(int i = n; i > 0; i-=2) {
            answer += i % 2 == 1 ? i : i*i;
        }
        return answer;
    }
```





## 4.1. 조건 문자열

![image-20240520182947531](/images/2024-05-16-practice-programmers-4/image-20240520182947531.png)

![image-20240520183049489](/images/2024-05-16-practice-programmers-4/image-20240520183049489.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(String ineq, String eq, int n, int m) {
        int answer = 0;
        switch(ineq) {
            case "<":
                switch(eq) {
                    case "=":
                        if(n <= m) answer = 1;
                        break;
                    case "!":
                        if(n < m) answer = 1;
                        break;
                }
                break;
            case ">":
                switch(eq) {
                    case "=":
                        if(n >= m) answer = 1;
                        break;
                    case "!":
                        if(n > m) answer = 1;
                        break;
                }
                break;
            default:
                answer = 0;
        }
        return answer;
    }
}
```





## 5.1. flag에 따라 다른 값 반환하기

![image-20240520183223360](/images/2024-05-16-practice-programmers-4/image-20240520183223360.png)

## 5.2. 풀이

```java
class Solution {
    public int solution(int a, int b, boolean flag) {
        int answer = answer = flag ? a+b : a-b;
        return answer;
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
