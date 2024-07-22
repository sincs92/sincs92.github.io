---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 10일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-22 18:43:04 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 문자열 앞의 n글자

![image-20240722184338845](/images/2024-07-22-practice-programmers-10/image-20240722184338845.png)



## 1.2. 풀이

```java
class Solution {
    public String solution(String my_string, int n) {
		return my_string.substring(0, n);
	}
}
```







## 2.1. 접두사인지 확인하기

![image-20240722185146155](/images/2024-07-22-practice-programmers-10/image-20240722185146155.png)

## 2.2. 풀이



```java
class Solution {
    public int solution(String my_string, String is_prefix) {
		return my_string.startsWith(is_prefix) ? 1 : 0;
	}
}
```





## 3.1. 문자열 뒤집기

![image-20240722185846953](/images/2024-07-22-practice-programmers-10/image-20240722185846953.png)



## 3.2. 풀이

```java
class Solution {
    public String solution(String my_string, int s, int e) {
    	// s인덱스부터 e인덱스 까지 뒤집기
    	int start = s;
    	int end = e;
    	char[] charArr = my_string.toCharArray();
    	
    	while(start < end) {
    		char temp = charArr[start];
    		charArr[start] = charArr[end];
    		charArr[end] = temp;
    		start++;
    		end--;
    	}
    	
    	StringBuilder sb = new StringBuilder();
    	for(char c : charArr) {
    		sb.append(c);
    	}
    	
		return sb.toString();
	}
    
}
```



문자 배열(char[])을 문자열로 바꾸는 데, 지금까지는 StringBuilder와 반복문을 이용했으나, 아래의 방법이 더 간편하고 오버헤드가 적은 것으로 보인다.

```java
class Solution {
    public String solution(String my_string, int s, int e) {
    	// s인덱스부터 e인덱스 까지 뒤집기
    	int start = s;
    	int end = e;
    	char[] charArr = my_string.toCharArray();
    	
    	while(start < end) {
    		char temp = charArr[start];
    		charArr[start] = charArr[end];
    		charArr[end] = temp;
    		start++;
    		end--;
    	}
    	
    	//StringBuilder sb = new StringBuilder();
    	//for(char c : charArr) {
    	//	sb.append(c);
    	//}
    	
		//return sb.toString();
        
        return new String(charArr);
	}
    
}
```





## 4.1. 세로 읽기

![image-20240722192327279](/images/2024-07-22-practice-programmers-10/image-20240722192327279.png)



## 4.2. 풀이

```java
class Solution {
    public String solution(String my_string, int m, int c) {
    	// 2차원 배열 이용
    	// { {i, h, r, h}, 
    	//   {b, a, k, r},
    	//   {f, p, n, d},
    	//   {o, p, l, j},
    	//   {h, y, g, c}
    	// }
    	char[][] twoDimArr = new char[my_string.length() / m][m];
    	
    	for(int i = 0; i < my_string.length(); i += m) {
    		char[] charArr = my_string.substring(i, i+m).toCharArray();
    		for(int j = 0; j < m; j++) {
    			twoDimArr[i/m][j] = charArr[j];
    		}
    	}
    	
    	StringBuilder sb = new StringBuilder();
    	
    	for(int i = 0; i < twoDimArr.length; i++) {
    		sb.append(twoDimArr[i][c-1]);
    	}
    	
    	return sb.toString();
    }
}
```



풀이 후 다른 사람들이 공유한 코드를 보니 나처럼 2차원 배열을 사용한 사람도 있었지만, 굳이 사용할 필요는 없었는 듯 하다. 그래도 연습한 셈 치고 다시 간단한 방식으로 풀어보았다.



```java
class Solution {
    public String solution(String my_string, int m, int c) {
    	StringBuilder sb = new StringBuilder();
    	for(int i = c-1; i < my_string.length(); i += m) {
    		sb.append(my_string.charAt(i));
    	}
    	return sb.toString();
    }
}
```







## 5.1. qr 코드

![image-20240722201040145](/images/2024-07-22-practice-programmers-10/image-20240722201040145.png)



## 5.2. 풀이

```java
class Solution {
    public String solution(int q, int r, String code) {
    	StringBuilder sb = new StringBuilder();
    	for(int i = 0; i < code.length(); i++) {
    		if(i % q == r) {
    			sb.append(code.charAt(i));
    		}
    	}
    	return sb.toString();
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
