---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 7일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-05-29 18:27:00 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 수열과 구간 쿼리 4

![image-20240529165837016](/images/2024-05-29-practice-programmers-7/image-20240529165837016.png)

![image-20240529165849374](/images/2024-05-29-practice-programmers-7/image-20240529165849374.png)

## 1.2. 풀이

```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        for(int[] query : queries) {
            int s = query[0];
            int e = query[1];
            int k = query[2];
            
            for(int i = s; i <= e; i++) {
                arr[i] = i % k == 0 ? arr[i] + 1 : arr[i];
            }
        }
        return arr;
    }
}
```





## 2.1. 배열 만들기 2

![image-20240529174036133](/images/2024-05-29-practice-programmers-7/image-20240529174036133.png)

![image-20240529174051328](/images/2024-05-29-practice-programmers-7/image-20240529174051328.png)



## 2.2. 풀이

```java
class Solution {
    public int[] solution(int l, int r) {
        int[] answer;
        String resultStr = "";
        for(int i = l; i <= r; i++) {
            String temp = String.valueOf(i);
            char[] tempCharArray = temp.toCharArray();
            boolean isIncluded = true;
            for(char tempChar : tempCharArray) {
            	if(!(tempChar == '0' || tempChar == '5')) {
            		isIncluded = false;
            		break;
            	}
            }
            if(isIncluded) {
                resultStr += temp + ",";
            }
        }
        if(resultStr == "" || resultStr.length() == 0) {
        	answer = new int[1];
        	answer[0] = -1;
        } else {
        	String[] strArr = resultStr.substring(0, resultStr.length() - 1).split(",");
        	answer = new int[strArr.length];
        	for(int i = 0; i < strArr.length; i++) {
        		answer[i] = Integer.parseInt(strArr[i]);
        	}
        }
                                        
        return answer;
    }
}
```







## 3.1. 카운트 업

![image-20240529175232829](/images/2024-05-29-practice-programmers-7/image-20240529175232829.png)

![image-20240529175247594](/images/2024-05-29-practice-programmers-7/image-20240529175247594.png)

## 3.2. 풀이

```java
class Solution {
    public int[] solution(int start_num, int end_num) {
        int[] answer = new int[end_num - start_num + 1];
        for(int i = 0; i < answer.length; i++) {
            answer[i] = start_num + i;
        }
        return answer;
    }
}
```



## 4.1. 콜라츠 수열 만들기

![image-20240529180526537](/images/2024-05-29-practice-programmers-7/image-20240529180526537.png)

![image-20240529180555574](/images/2024-05-29-practice-programmers-7/image-20240529180555574.png)

## 4.2. 풀이

```java
class Solution {
    public int[] solution(int n) {
        int[] answer = {};
        String tempStr = n + ",";
        while(n > 1) {
            if(n % 2 == 0) {
                n /= 2;
            } else {
                n = 3 * n + 1;
            }
            tempStr += n + ",";
        }
        String[] tempStrArr = tempStr.substring(0, tempStr.length() - 1).split(",");
        answer = new int[tempStrArr.length];
        for(int i = 0; i < tempStrArr.length; i++) {
            answer[i] = Integer.parseInt(tempStrArr[i]);
        }
        return answer;
    }
}
```





## 5.1. 배열 만들기 4

![image-20240529180831772](/images/2024-05-29-practice-programmers-7/image-20240529180831772.png)

![image-20240529180849766](/images/2024-05-29-practice-programmers-7/image-20240529180849766.png)

## 5.2. 풀이

```java
import java.util.ArrayList;

class Solution {
    public int[] solution(int[] arr) {
        int[] stk = {};
        ArrayList<Integer> list = new ArrayList();
        for(int i = 0; i < arr.length; i++) {
            if(list.size() == 0) {
                list.add(arr[i]);
            } else {
                if(list.size() != 0 && list.get(list.size() - 1) < arr[i]){
                    list.add(arr[i]);
                } else if(list.size() != 0 && list.get(list.size() - 1) >= arr[i]) {
                    list.remove(list.size() - 1);
                    i--;
                }
            }
        }
        stk = new int[list.size()];
        for(int i = 0; i < stk.length; i++) {
            stk[i] = list.get(i);
        }
        return stk;
    }
}
```



> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
