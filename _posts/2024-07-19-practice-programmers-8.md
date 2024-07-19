---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 8일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-19 17:00:23 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 간단한 논리 연산

![image-20240606174255224](/images/2024-06-06-practice-programmers-8/image-20240606174255224.png)

## 1.2. 풀이

```java
class Solution {
    public boolean solution(boolean x1, boolean x2, boolean x3, boolean x4) {
    	return (x1 || x2 ) && (x3 || x4) ? true : false;
    }
}
```





## 2.1. 주사위 게임 3

![image-20240607161913505](/images/2024-06-06-practice-programmers-8/image-20240607161913505.png)

![image-20240607161932836](/images/2024-06-06-practice-programmers-8/image-20240607161932836.png)

## 2.2. 풀이

최초의 답안

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;
import java.util.function.Consumer;

class Solution {
    public int solution(int a, int b, int c, int d) {
    	// 같을 경우
    	if (a==b&&b==c&&c==d) {
    		int p = a;
    		return 1111 * p;
    	} else if ((a==b && b==c && c!=d) 
    			|| (a==b && b==d && d!=c) 
    			|| (a==d && c==d && a!=b) 
    			|| (b==c && c==d && d!=a)
			) {
    		int q = 
    				(a==b && b==c && c!=d) ? d 
    				: (a==b && b==d && d!=c) ? c 
					: (a==d && c==d && a!=b) ? b 
					: a;
    		int p = 
    				(a==b && b==c && c!=d) ? a 
    				: (a==b && b==d && d!=c) ? b 
					: (a==d && c==d && a!=b) ? c 
					: d;
    		return (10 * p + q) * (10 * p + q);
    	} else if((a==b&&c==d)
			||(a==c&&b==d)
			||(a==d&&b==c)
			) {
    		int p = a;
    		int q = a==d ? c : d;
    		return (p+q) * Math.abs(p-q);
    	} else if((a==b&&a!=c&&a!=d)
			|| (a==c&&a!=b&&a!=d)
			|| (a==d&&a!=b&&a!=c)
			|| (b==c&&b!=d&&b!=a)
			|| (b==d&&b!=a&&b!=c)
			|| (c==d&&c!=a&&c!=b)
			) {
    		return (a==b&&a!=c&&a!=d) ? c * d
    				: (a==c&&a!=b&&a!=d) ? b * d
					: (a==d&&a!=b&&a!=c) ? b * c
					: (b==c&&b!=d&&b!=a) ? d * a
					: (b==d&&b!=a&&b!=c) ? a * c
					: a*b;
    		
    	} else {
    		List<Integer> list = Arrays.asList(a,b,c,d);
    		return Collections.min(list);
    	}
    	
    }
}
```



정렬로 다시 풀어본 답안

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

class Solution {
   public int solution(int a, int b, int c, int d) {
    	int answer = 0;
    	int[] dice = {a,b,c,d};
    	Arrays.sort(dice);
    	// 정렬 후에 처음과 끝이 같으면 모두 같은 수
    	if(dice[0] == dice[3]) {
    		answer = dice[0] * 1111;
    	} else if (dice[0] != dice[1] && dice[1] == dice[2] && dice[2] == dice[3]) {
    		answer = (int)(Math.pow(10 * dice[1] + dice[0], 2));
    	} else if (dice[2] != dice[3] && dice[0] == dice[1] && dice[1] == dice[2]) {
    		answer = (int)(Math.pow(10 * dice[1] + dice[3], 2));
    	} else if (dice[0] == dice[1] && dice[2] == dice[3]) {
			answer = (dice[0] + dice[2]) * Math.abs(dice[0] - dice[2]);
    	} else if (dice[0] == dice[1]) {
			answer = dice[2] * dice[3];
    	} else if (dice[1] == dice[2]) {
			answer = dice[0] * dice[3];
    	} else if (dice[2] == dice[3]) {
			answer = dice[0] * dice[1]; 
    	} else {
    		answer = dice[0];
    	}
    	return answer;
    }
}
```



더 간단한 방법 (https://school.programmers.co.kr/questions/74936)을 바탕으로 다시 푼 답안

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int solution(int a, int b, int c, int d) {
    	int answer = 0;
    	int[] dice = {a,b,c,d};
    	Arrays.sort(dice);
    	a = dice[0]; b = dice[1]; c = dice[2]; d = dice[3];
    	return
    			a==d ? a * 1111 :
    			a==c ? (10 * a + d) * (10 * a + d) :
    			b==d ? (10 * b + a) * (10 * b + a) :
    			a==b&&c==d ? (a+c) * Math.abs(a-c) :
    			a==b ? c*d :
				c==d ? a*b :
				b==c ? a*d : a;
    }
}
```









## 3.1. 글자 이어 붙여 문자열 만들기

![image-20240607175055817](/images/2024-06-06-practice-programmers-8/image-20240607175055817.png)

![image-20240607175108976](/images/2024-06-06-practice-programmers-8/image-20240607175108976.png)



## 3.2. 풀이

```java
class Solution {
    public String solution(String my_string, int[] index_list) {
        char[] stringToChar = my_string.toCharArray();
        char[] resultCharArr = new char[index_list.length];
        for(int i = 0; i < index_list.length; i++) {
        	resultCharArr[i] = stringToChar[index_list[i]];
        }
        return new String(resultCharArr);
    }
}
```



## 4.1. 9로 나눈 나머지

![image-20240719180608497](/images/2024-07-19-practice-programmers-8/image-20240719180608497.png)

## 4.2. 풀이

```java
class Solution {
    public int solution(String number) {
        char[] strToChar = number.toCharArray();
        int sum = 0;
        for(char c : strToChar) {
            sum += Integer.valueOf(String.valueOf(c));
        }
        return sum % 9;
    }
}
```





## 5.1. 문자열 여러 번 뒤집기

![image-20240719163357800](/images/2024-06-06-practice-programmers-8/image-20240719163357800.png)



## 5.2. 풀이

```java
class Solution {
    public String solution(String my_string, int[][] queries) {
        String answer = "";
        char[] stringToChar = my_string.toCharArray();
        for(int i = 0; i < queries.length; i++) {
        	int[] query = queries[i];
        	// query[0]부터 query[1]까지 뒤집는다.
        	// 1. query[0]부터 query[1]까지 역순으로 문자열로 합치고, 다시 문자 배열로 나누어서 기존 배열의 인덱스에 대입
        	StringBuilder sb = new StringBuilder();
        	for(int j = query[1]; j >= query[0]; j--) {
        		sb.append(stringToChar[j]);
        	}
        	// 뒤집어진 부분의 문자열을 문자 배열로 변환 후 전체 문자배열 해당 인덱스에 대입
        	String reversedStr = sb.toString();
        	char[] reversedCharArr = reversedStr.toCharArray();
        	for(int k = 0; k < reversedCharArr.length; k++) {
        		stringToChar[k+query[0]] = reversedCharArr[k];
        	}
        }
        
        StringBuilder sbRes = new StringBuilder();
        for(char c : stringToChar) {
        	sbRes.append(c);
        }
        answer = sbRes.toString();
        return answer;
    }
}
```



다른 사람의 풀이 (https://school.programmers.co.kr/learn/courses/30/lessons/181913/solution_groups?language=java)를 바탕으로 다시 푼 답안



```java
class Solution {
    public String solution(String my_string, int[][] queries) {
        char[] charArr = my_string.toCharArray();
        for(int i = 0; i < queries.length; i++) {
        	int[] query = queries[i];
        	int start = query[0];
        	int end = query[1];
        	reverse(charArr, start, end);
        }
        return new String(charArr);
    }
    
	private void reverse(char[] charArr, int start, int end) {
		char temp = 0;
		while(start < end) {
			temp = charArr[start];
			charArr[start] = charArr[end];
			charArr[end] = temp;
			start++;
			end--;
		}
	}
}
```









> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
