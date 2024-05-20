---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 5일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-20 18:34:00 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 코드 처리하기



![image-20240520192225048](/images/2024-05-16-practice-programmers-5/image-20240520192225048.png)

![image-20240520192252742](/images/2024-05-16-practice-programmers-5/image-20240520192252742.png)

## 1.2. 풀이

```java
class Solution {
    public String solution(String code) {
        int mode = 0;
        String ret = "";
        for(int idx = 0; idx < code.length(); idx++) {
        	String tempStr = Character.toString(code.charAt(idx));
        	if(tempStr.equals("1")) {
        		mode = mode == 0 ? 1 : 0;
        	} else {
        		if(mode == 0 && idx % 2 == 0 || mode == 1 && idx % 2 == 1) {
        			ret += tempStr;
        		}
        	}
        }
        return !ret.equals("") ? ret : "EMPTY";
    }
}
```



```java
if(mode == 0 && idx % 2 == 0 || mode == 1 && idx % 2 == 1) {
    ...
}
```

이 부분을

```java
if(idx % 2 == mode) {
    ...
}
```

이렇게도 줄일 수 있을 것 같다.





## 2.1. 등차수열의 특정한 항만 더하기

![image-20240520195937740](/images/2024-05-16-practice-programmers-5/image-20240520195937740.png)

![image-20240520195953305](/images/2024-05-16-practice-programmers-5/image-20240520195953305.png)

## 2.2. 풀이

```java
class Solution {
    public int solution(int a, int d, boolean[] included) {
        int answer = 0;
        int[] apArr = new int[included.length];
        for(int i = 0; i < apArr.length; i++) {
        	apArr[i] = i == 0 ? a : apArr[i-1] + d;
    		answer += included[i] ? apArr[i] : 0; 
        }
        return answer;
    }
}
```



```java
import java.util.stream.IntStream;

class Solution {
    public int solution(int a, int d, boolean[] included) {
        return IntStream.range(0, included.length)
                        .map(idx -> included[idx] ? a + (idx * d) : 0)
                        .sum();
    }
}
```

아래는 다른 사람이 짠 코드인데, IntStream이 무엇인지 다음에 알아보아야겠다.





## 3.1. 주사위 게임 2

![image-20240520203253473](/images/2024-05-16-practice-programmers-5/image-20240520203253473.png)

![image-20240520203304494](/images/2024-05-16-practice-programmers-5/image-20240520203304494.png)



## 3.2. 풀이

```java
class Solution {
    public int solution(int a, int b, int c) {
        int answer = 1;
        int count = 0;

        if(a==b && b == c) {
        	count += 3;
        } else {
        	if(a==b || b==c || a==c) {
        		count += 2;
        	} else {
        		count += 1;
        	}
        }
        
        for(int i = 1; i <= count; i++) {
        	answer *= (a * (int)Math.pow(a, i-1)) + (b * (int)Math.pow(b, i-1)) + (c * (int)Math.pow(c, i-1)); 
        }
        
        return answer;
        
    }
}
```



## 4.1. 원소들의 곱과 합

![image-20240520210522030](/images/2024-05-16-practice-programmers-5/image-20240520210522030.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(int[] num_list) {
        int multi = 1;
        int sum = 0;
        int sumSq = 0;
        for(int i = 0; i < num_list.length; i++) {
            multi *= num_list[i];
            sum += num_list[i];
        }
        sumSq = (int)Math.pow(sum, 2);
        return multi < sumSq ? 1 : 0;
    }
}
```





## 5.1. 이어 붙인 수

![image-20240520183223360](/images/2024-05-16-practice-programmers-5/image-20240520210859490.png)

![image-20240520210917532](/images/2024-05-16-practice-programmers-5/image-20240520210917532.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        String oddSum = "";
        String evenSum = "";
        for(int i = 0; i < num_list.length; i++) {
            if(num_list[i] % 2 == 1) {
                oddSum += String.valueOf(num_list[i]);    
            } else {
                evenSum += String.valueOf(num_list[i]);
            }
        }
        answer = Integer.valueOf(oddSum) + Integer.valueOf(evenSum);
        return answer;
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
