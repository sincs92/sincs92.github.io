---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 9일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-19 18:37:17 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 배열 만들기 5

![image-20240719170200849](/images/2024-07-19-practice-programmers-9/image-20240719170200849.png)



## 1.2. 풀이

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int[] solution(String[] intStrs, int k, int s, int l) {
    	List<Integer> arrList = new ArrayList<Integer>();

    	for(String str : intStrs) {
    		int subInt = Integer.parseInt(str.substring(s, s+l));
    		if(subInt > k) {
    			arrList.add(subInt);
    		}
    	}
        int[] answer = new int[arrList.size()];
	    for (int i = 0 ; i < arrList.size() ; i++) {
	    	answer[i] = arrList.get(i).intValue();
	    }
    	
		return answer;
	}
}
```



## 1.3. 참고

- **parseInt()와 intValue()**

  [https://java119.tistory.com/30](https://java119.tistory.com/30)

- **Integer ArrayList를 int 배열로 변환하기**

  [https://velog.io/@deannn/Java-int%ED%98%95-ArrayList-%EB%B0%B0%EC%97%B4-%EB%B3%80%ED%99%98](https://velog.io/@deannn/Java-int%ED%98%95-ArrayList-%EB%B0%B0%EC%97%B4-%EB%B3%80%ED%99%98)



## 2.1. 부분 문자열 이어 붙여 문자열 만들기

![image-20240719174728311](/images/2024-07-19-practice-programmers-9/image-20240719174728311.png)

## 2.2. 풀이



```java
class Solution {
    public String solution(String[] my_strings, int[][] parts) {
    	
    	StringBuilder sb = new StringBuilder();
    	
    	for(int i = 0; i < parts.length; i++) {
    		int[] part = parts[i];
    		String str = my_strings[i];
    		sb.append(str.substring(part[0], part[1]+1));
    	}
    	
		return sb.toString();
	}
}
```





## 3.1. 문자열 뒤의 n글자

![image-20240719180002769](/images/2024-07-19-practice-programmers-9/image-20240719180002769.png)



## 3.2. 풀이

```java
class Solution {
    public String solution(String my_string, int n) {
		return my_string.substring(my_string.length()-n);
	}
}
```



## 4.1. 접미사 배열

![image-20240719181638593](/images/2024-07-19-practice-programmers-9/image-20240719181638593.png)



## 4.2. 풀이

```java
import java.util.Arrays;

class Solution {
    public String[] solution(String my_string) {
    	String[] strArr = new String[my_string.length()];
    	for(int i = 0; i < strArr.length; i++) {
    		strArr[i] = my_string.substring(i);
    	}
    	Arrays.sort(strArr);
		return strArr;
	}
}
```





## 5.1. 접미사인지 확인하기

![image-20240719182437345](/images/2024-07-19-practice-programmers-9/image-20240719182437345.png)



## 5.2. 풀이

```java
class Solution {
    public int solution(String my_string, String is_suffix) {
    	int result = 0;
    	for(int i = 0; i < my_string.length(); i++) {
    		if(my_string.substring(i).equals(is_suffix)) result = 1;
    	}
		return result;
	}
}
```



```java
class Solution {
    public int solution(String my_string, String is_suffix) {
		return my_string.endsWith(is_suffix) ? 1 : 0;
	}
}
```



## 5.3 참고

- **startsWith(), endsWith()** 

  [https://jamesdreaming.tistory.com/86](https://jamesdreaming.tistory.com/86)





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
