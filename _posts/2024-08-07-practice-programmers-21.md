---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 21일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-07 20:44:36 +09:00
typora-root-url: ../
published: false
---







# 1. 문제



## 1.1. 배열의 길이를 2의 거듭제곱으로 만들기

![image-20240807170016170](/images/2024-08-06-practice-programmers-20/image-20240807170016170.png)



## 1.2. 풀이

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] arr) {
    	int needNum = powerOfTwo(arr.length);
    	
    	if(needNum == 0) {
    		return arr;
    	} else {
    		int[] answer = Arrays.copyOf(arr, arr.length + needNum);
    		return answer;
    	}
    }
    
    public int powerOfTwo(int num) {
    	if(num == 1) {
    		return 0;
    	}
    	
    	int idx = 2;
    	
    	while(idx < num) {
    		idx *= 2;
    	}
    	
    	if(num == idx) {
    		return 0;
    	} else {
    		return idx - num;
    	}
    }
}
```



풀고나서 보니 불필요한 코드가 있어 제거했다.

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] arr) {
    	int needNum = powerOfTwo(arr.length);
    	
    	if(needNum == 0) {
    		return arr;
    	} else {
    		int[] answer = Arrays.copyOf(arr, arr.length + needNum);
    		return answer;
    	}
    }
    
    public int powerOfTwo(int num) {
    	int idx = 1;
    	
    	while(idx < num) {
    		idx *= 2;
    	}
    		return idx - num;
    }
}
```



## 2.1. 배열 비교하기

![image-20240807173204799](/images/2024-08-06-practice-programmers-20/image-20240807173204799.png)





## 2.2. 풀이

```java
class Solution {
    public int solution(int[] arr1, int[] arr2) {
    	
    	if(arr1.length != arr2.length) {
    		return arr1.length > arr2.length ? 1 : -1;
    	} else {
    		int arrSum1 = 0;
    		int arrSum2 = 0;
    		
    		for(int a : arr1) arrSum1 += a;
    		for(int b : arr2) arrSum2 += b;
    		
    		if(arrSum1 == arrSum2) {
    			return 0;
    		} else {
    			return arrSum1 > arrSum2 ? 1 : -1;
    		}
    	}
    }
}
```





## 3.1. 문자열 묶기

![image-20240807174912892](/images/2024-08-06-practice-programmers-20/image-20240807174912892.png)



## 3.2. 풀이

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int solution(String[] strArr) {
    	// 문자열 배열 strArr이 주어집니다. 
    	// strArr의 원소들을 길이가 같은 문자열들끼리 그룹으로 묶었을 때 가장 개수가 많은 그룹의 크기를 return 하는 
    	// solution 함수를 완성해 주세요.
    	Map<Integer, String> map = new HashMap<Integer, String>();
    	for(String i : strArr) {
    		if(!map.containsKey(i.length())) {
    			map.put(i.length(), "");
    		}
    	}
    	
    	int[] lenArr = new int[map.size()];
    	for(int i = 0; i < lenArr.length; i++) {
    		lenArr[i] = i+1;
    	}
    	
    	for(int i = 0; i < strArr.length; i++) {
    		for(int j = 0; j < lenArr.length; j++) {
    			boolean isInclude = false;
    			if(strArr[i].length() == lenArr[j]) {
    				isInclude = true;
    			}
    			if(isInclude) {
    				String temp = "";
    				if(map.get(strArr[i].length()).equals("")) {
    					temp = strArr[i];
    					temp += ",";
    					map.put(strArr[i].length(), temp);
    				} else {
    					temp = map.get((strArr[i].length()));
    					temp += strArr[i];
    					temp += ",";
    					map.put(strArr[i].length(), temp);
    				}
    			}
    		}
    	}
    	
    	int max = 1;
    	
    	for (int key : map.keySet()) {
    		int value = map.get(key).toString().split(",").length;
    		
    		if(value > max) {
    			max = value;
    		}
    	}
    	
    	return max;

    }
}
```





## 4.1. 배열의 길이에 따라 다른 연산하기

![image-20240807191652403](/images/2024-08-06-practice-programmers-20/image-20240807191652403.png)



## 4.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr, int n) {
    	for(int i = 0; i < arr.length; i++) {
    		if(arr.length % 2 == 0) {
    			if(i % 2 > 0) {
					arr[i] += n;
				}
    		} else {
    			if(i % 2 == 0) {
					arr[i] += n;
				}
    		}
    	}
    	
    	return arr;
    }
}
```





## 5.1. 뒤에서 5등까지

![image-20240807193543364](/images/2024-08-06-practice-programmers-20/image-20240807193543364.png)



## 5.2. 풀이

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] num_list) {
    	Arrays.sort(num_list);
    	return Arrays.copyOf(num_list, 5);
    }
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
