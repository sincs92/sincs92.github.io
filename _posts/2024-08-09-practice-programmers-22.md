---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 22일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-09 18:28:20 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 0 떼기

![image-20240808195234651](/images/2024-08-09-practice-programmers-22/image-20240808195234651.png)



## 1.2. 풀이

```java
class Solution {
    public String solution(String n_str) {
    	char[] charArr = n_str.toCharArray();
    	int idx = 0;
    	
    	for(int i = 0; i < charArr.length; i++) {
    		if(charArr[i] != '0') {
    			if(i == 0) {
    				break;
    			}
    			idx = i;
                break;
    		}
    	}
    	
		return n_str.substring(idx);
	}
}
```



아래는 다른 사람들의 풀이를 참조해 다시 푼 답

```java
    public String solution(String n_str) {
        return "" + Integer.parseInt(n_str);
    }
```





## 2.1. 두 수의 합

![image-20240808195300436](/images/2024-08-09-practice-programmers-22/image-20240808195300436.png)





## 2.2. 풀이

```java
import java.math.BigInteger;

class Solution {
    public String solution(String a, String b) {
        return "" + new BigInteger(a).add(new BigInteger(b));
    }
}
```



참고: [https://dreamcoding.tistory.com/73](https://dreamcoding.tistory.com/73)





## 3.1. 문자열로 변환

![image-20240808195328342](/images/2024-08-09-practice-programmers-22/image-20240808195328342.png)



## 3.2. 풀이

```java
class Solution {
    public String solution(int n) {
        return ""+n;
    }
}

```



## 4.1. 배열의 원소 삭제하기

![image-20240808195402351](/images/2024-08-09-practice-programmers-22/image-20240808195402351.png)



## 4.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;
​
class Solution {
    public int[] solution(int[] arr, int[] delete_list) {
        List<Integer> list = new ArrayList<Integer>();
        
        for(int i = 0; i < arr.length; i++) {
            boolean isDeleted = false;
            
            for(int j = 0; j < delete_list.length; j++) {
                if(arr[i] == delete_list[j]) {
                    isDeleted = true;
                }
            }
            
            if(!isDeleted) {
                list.add(arr[i]);
            }
        }
        
        int[] answer =  new int[list.size()];
        
        for(int i = 0; i < answer.length; i++) {
            answer[i] = list.get(i);
        }
        
        return answer;
    }
}
```







## 5.1. 부분 문자열인지 확인하기

![image-20240808195433966](/images/2024-08-09-practice-programmers-22/image-20240808195433966.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(String my_string, String target) {
        return my_string.contains(target) ? 1 : 0;
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
