---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 3일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-16 20:19:00 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 문자열 섞기

![image-20240516191819222](/images/2024-05-16-practice-programmers-3/image-20240516191819222.png)



## 1.2. 풀이

```java
class Solution {
    public String solution(String str1, String str2) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        String[] str1Arr = str1.split("");
        String[] str2Arr = str2.split("");
        
        for(int i = 0; i < str1Arr.length; i++) {
            sb.append(str1Arr[i]);
            sb.append(str2Arr[i]);
        }
        answer += sb.toString();
        
        return answer;
    }
}
```

최초 풀이



```java
class Solution {
    public String solution(String str1, String str2) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        
        for(int i = 0; i < str1.length(); i++) {
            sb.append(str1.charAt(i)).append(str2.charAt(i));
        }
        answer += sb.toString();
        
        return answer;
    }
}
```



문자열을 배열로 바꾸는 것은 오버헤드가 크므로 가능하면 아래와 같은 방법을 사용하는 편이 성능적으로 효율적일 것으로 나아보인다.



## 2.1. 문자 리스트를 문자열로 변환하기

![image-20240516193657058](/images/2024-05-16-practice-programmers-3/image-20240516193657058.png)





## 2.2. 풀이

```java
class Solution {
    public String solution(String[] arr) {
        return String.join("", arr);
    }
}
```





## 3.1. 문자열 곱하기

![image-20240516194144894](/images/2024-05-16-practice-programmers-3/image-20240516194144894.png)

![image-20240516194207936](/images/2024-05-16-practice-programmers-3/image-20240516194207936.png)



## 3.2. 풀이

```java
class Solution {
    public String solution(String my_string, int k) {
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < k; i++) {
            sb.append(my_string);
        }
        return sb.toString();
    }
}
```



```java
class Solution {
    public String solution(String my_string, int k) {
        return my_string.repeat(k);
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
