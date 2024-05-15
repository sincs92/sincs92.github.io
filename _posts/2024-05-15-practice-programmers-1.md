---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 문제 1일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-15 20:37:23 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 문자열 출력하기

![image-20240515203052724](/images/2024-05-15-practice-programmers (copy)/image-20240515203052724.png)



## 1.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        System.out.print(str);
        sc.close();
        
    }
}
```



## 2.1. a와 b 출력하기

![image-20240515203355109](/images/2024-05-15-practice-programmers (copy)/image-20240515203355109.png)

![image-20240515211415997](/images/2024-05-15-practice-programmers-1/image-20240515211415997.png)

## 2.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        System.out.println("a = " + Integer.toString(a));
        System.out.println("b = " + Integer.toString(b));

        
    }
}
```





## 3.1. 문자열 반복해서 출력하기

![image-20240515190906171](/images/2024-05-15-practice-programmers (copy)/image-20240515190906171.png)

![image-20240515190946737](/images/2024-05-15-practice-programmers (copy)/image-20240515190946737.png)





## 3.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        int n = sc.nextInt();
        StringBuilder sb = new StringBuilder();
        for(int i = 1; i <= n; i++) {
            sb.append(str);
        }
        String result = sb.toString();
        System.out.println(result);        
    }
}
```



불변인 String은 문자열이 더해질때마다 새로운 객체를 생성하기 때문에 성능을 고려해 StringBuilder를 채택하였다.



- [ ] **String과 StringBuilder, 그리고 StringBuffer의 차이** (추가 예정)





## 4.1. 대소문자 바꿔서 출력하기

![image-20240515193717309](/images/2024-05-15-practice-programmers (copy)/image-20240515193717309.png)

![image-20240515193830493](/images/2024-05-15-practice-programmers (copy)/image-20240515193830493.png)



## 4.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        StringBuilder sb = new StringBuilder();
        // String을 char형 배열로 
        char[] charArr = a.toCharArray();
        
        boolean isUpper = false;
        for(int i = 0; i < charArr.length; i++){
            isUpper = (Character.isUpperCase(charArr[i])) ? true : false;         
            // 인덱스가 대문자라면?
            if(isUpper) {
                sb.append(Character.toString(charArr[i]).toLowerCase());
            // 인덱스가 소문자라면?
            } else {
                sb.append(Character.toString(charArr[i]).toUpperCase());
            }
        }
        String result = sb.toString();
        System.out.println(result);
    }
}
```



## 5.1. 특수문자 출력하기

![image-20240515200958818](/images/2024-05-15-practice-programmers (copy)/image-20240515200958818.png)



## 5.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        System.out.println("!@#$%^&*(\\'\"<>?:;");
    }
}
```







> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
