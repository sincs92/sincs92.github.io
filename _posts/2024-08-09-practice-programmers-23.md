---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 23일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-09 20:21:00 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 부분 문자열

![image-20240809183109539](/images/2024-08-09-practice-programmers-23/image-20240809183109539.png)



## 1.2. 풀이

```java
class Solution {
    public int solution(String str1, String str2) {
        return str2.contains(str1) ? 1 : 0;
    }
}
```





## 2.1. 꼬리 문자열

![image-20240809183140761](/images/2024-08-09-practice-programmers-23/image-20240809183140761.png)





## 2.2. 풀이

```java
class Solution {
    public String solution(String[] str_list, String ex) {
        StringBuilder sb = new StringBuilder();
        
        for(int i = 0; i < str_list.length; i++) {
            if(!str_list[i].contains(ex)) {
                sb.append(str_list[i]);
            }
        }
        
        return sb.toString();
    }
}
```







## 3.1. 정수 찾기

![image-20240809183211356](/images/2024-08-09-practice-programmers-23/image-20240809183211356.png)



## 3.2. 풀이

```java
class Solution {
    public int solution(int[] num_list, int n) {
    	
    	for(int i : num_list) {
    		if(i == n) {
    			return 1;
    		}
    	}
    	
    	return 0;
	}
}
```





## 4.1. 주사위 게임 1

![image-20240809183236878](/images/2024-08-09-practice-programmers-23/image-20240809183236878.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(int a, int b) {
    	if(a % 2 > 0 || b % 2 > 0) {
    		if(a % 2 > 0 && b % 2 > 0) {
    			return (int) (Math.pow(a, 2) + Math.pow(b, 2));
    		} else {
    			return 2 * (a + b);
    		}
    	} else {
    		return Math.abs(a - b);
    	}
    	
	}
}
```





## 5.1. 날짜 비교하기

![image-20240809183303072](/images/2024-08-09-practice-programmers-23/image-20240809183303072.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(int[] date1, int[] date2) {
    	String date1Str = "";
    	String date2Str = "";
    	for(int i : date1) {
    		date1Str += i;
    	}
    	for(int i : date2) {
    		date2Str += i;
    	}
    	
		return Integer.parseInt(date1Str) < Integer.parseInt(date2Str) ? 1 : 0;
	}
}
```



테스트는 통과했지만 비슷한 다른 사람의 풀이에 달린 댓글을 보고 잘못된 점을 파악했다.



2023년 5월 15과 2023년 11월 5일의 비교라면? 기댓값은 물론 전자가 이전 날짜이므로 1이다.

그러나 2023515 > 2023115로 실제로는 0이 나오게 된다.



날짜를 비교하는 데 있어서 이러한 점을 유의해야 겠다.



다음은 이것을 고려해 다시 짜본 코드이다.



```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

class Solution {
    public int solution(int[] date1, int[] date2) {
    	String date1Str = "";
    	String date2Str = "";
    	
    	for(int i : date1) {
    		date1Str += i + ",";
    	}
    	for(int i : date2) {
    		date2Str += i + ",";
    	}
    	
    	date1Str = date1Str.substring(0, date1Str.length()-1);
    	date2Str = date2Str.substring(0, date2Str.length()-1);
    	
    	Date date1Real;
    	Date date2Real;
    	SimpleDateFormat formatter = new SimpleDateFormat("yyyy,MM,dd");
		int answer = 0;
		
		try {
			date1Real = formatter.parse(date1Str);
			date2Real = formatter.parse(date2Str);
			return date1Real.getTime() < date2Real.getTime() ? 1 : 0;
		} catch (ParseException e) {
			return answer;
		}
		
	}
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
