---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 2일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-16 19:10:20 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 덧셈식 출력하기

![image-20240515204436798](/images/2024-05-16-practice-programmers-2/image-20240515204436798.png)

![image-20240515204503969](/images/2024-05-16-practice-programmers-2/image-20240515204503969.png)



## 1.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        int sum = a + b;
        System.out.println(a + " + " + b + " = " + sum);
    }
}
```





```java

import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();

        System.out.printf("%d + %d = %d",a,b,a+b);
    }
}
```



다른 사람들의 풀이를 보니 printf 메소드를 사용한 사람들이 많았다. 다음에는 printf를 사용해 문자열을 출력해봐야겠다.



## 2.1. 문자열 붙여서 출력하기

![image-20240515204926206](/images/2024-05-16-practice-programmers-2/image-20240515204926206.png)

![image-20240515204936763](/images/2024-05-16-practice-programmers-2/image-20240515204936763.png)



## 2.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        String b = sc.next();
        StringBuilder sb = new StringBuilder();
        sb.append(a);
        sb.append(b);
        System.out.println(sb.toString());
        
    }
}
```





## 3.1. 문자열 돌리기

![image-20240515205607581](/images/2024-05-16-practice-programmers-2/image-20240515205607581.png)

![image-20240515205617331](/images/2024-05-16-practice-programmers-2/image-20240515205617331.png)



## 3.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        String[] aArr = a.split("");
        for(String aa : aArr) {
            System.out.println(aa);
        }
        
    }
}
```





## 4.1. 홀짝 구분하기

![image-20240515210832590](/images/2024-05-16-practice-programmers-2/image-20240515210832590.png)

![image-20240515210845438](/images/2024-05-16-practice-programmers-2/image-20240515210845438.png)

## 4.2. 풀이

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        String result = (n % 2 == 0) ? n + " is even" : n + " is odd";
        System.out.println(result);
    }
}
```



```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        String result = n + " is " + ((n % 2 == 0) ? "even" : "odd");
        System.out.println(result);
    }
}
```





## 5.1. 문자열 겹쳐쓰기

![image-20240515211201059](/images/2024-05-16-practice-programmers-2/image-20240515211201059.png)

![image-20240515211232766](/images/2024-05-16-practice-programmers-2/image-20240515211232766.png)



## 5.2. 풀이

```java
class Solution {
    public String solution(String my_string, String overwrite_string, int s) {
        String answer = "";
        String[] mArr = my_string.split("");
        String[] oArr = overwrite_string.split("");
        StringBuilder sb = new StringBuilder();
        
        for(int i = 0; i < mArr.length; i++) {
            if(i >= s && (i-s) < oArr.length) {
                mArr[i] = oArr[i-s];
                sb.append(mArr[i]);
            } else { 
            	sb.append(mArr[i]);
            }

        }
        answer = sb.toString();   
        
        return answer;
    }
}
```

습관적으로 문자열을 배열로 바꾸어 for문을 이용해 수동으로 치환한 처음 방법 (가독성이 떨어진다.)



```java
class Solution {
    public String solution(String my_string, String overwrite_string, int s) {
        StringBuilder sb = new StringBuilder();
    	String answer = "";
        String before = my_string.substring(0, s);
        String after = my_string.substring(s + overwrite_string.length());
        sb.append(before).append(overwrite_string).append(after);
        answer += sb.toString();
        
        return answer;
    }
}
```

더 간단한 방법. 다른 사람들의 풀이를 참고했다. 







> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
