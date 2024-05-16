---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 문제 풀기 - 1"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-16 20:19:00 +09:00
typora-root-url: ../
published: false
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







## 4.1. 더 크게 합치기

![image-20240516194945598](/images/2024-05-16-practice-programmers-3/image-20240516194945598.png)





## 4.2. 풀이

```java
class Solution {
    public int solution(int a, int b) {
        int answer = 0;
        String aStr = Integer.toString(a);
        String bStr = Integer.toString(b);
        int x = Integer.valueOf(aStr + bStr);
        int y = Integer.valueOf(bStr + aStr);
        answer = (x >= y) ? x : y;
        return answer;
    }
}
```

삼항연산자를 이용한 풀이



```java
class Solution {
    public int solution(int a, int b) {
        String aStr = Integer.toString(a);
        String bStr = Integer.toString(b);
        int x = Integer.valueOf(aStr + bStr);
        int y = Integer.valueOf(bStr + aStr);
        return Math.max(x,y);
    }
}
```

Math의 max메소드를 이용한 풀이



## 5.1. 두 수의 연산 값 비교하기

![image-20240516200904111](/images/2024-05-16-practice-programmers-3/image-20240516200904111.png)

![image-20240516200923768](/images/2024-05-16-practice-programmers-3/image-20240516200923768.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(int a, int b) {
        int answer = 0;
        int op1 = Integer.parseInt("" + a + b);
        int op2 = 2 * a * b;
        answer = (op1 >= op2) ? op1 : op2;
        return answer;
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
