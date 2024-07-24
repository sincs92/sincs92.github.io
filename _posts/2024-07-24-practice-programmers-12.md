---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 12일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-24 17:30:35 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 리스트 자르기

![image-20240724173305927](/images/2024-07-24-practice-programmers-12/image-20240724173305927.png)



## 1.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int n, int[] slicer, int[] num_list) {
    	int a = slicer[0];
    	int b = slicer[1];
    	int c = slicer[2];
    	
    	List<Integer> list = new ArrayList<>();
    	switch(n) {
	    	case 1:
	    		// n = 1 : num_list의 0번 인덱스부터 b번 인덱스까지
	    		for(int i = 0; i <= b; i++) {
	    			list.add(num_list[i]);
	    		}
	    		break;
	    	case 2:
	    		// n = 2 : num_list의 a번 인덱스부터 마지막 인덱스까지
	    		for(int i = a; i <= num_list.length-1; i++) {
	    			list.add(num_list[i]);
	    		}
	    		break;
	    	case 3:
	    		// n = 3 : num_list의 a번 인덱스부터 b번 인덱스까지
	    		for(int i = a; i <= b; i++) {
	    			list.add(num_list[i]);
	    		}
	    		break;
	    	case 4:
	    		// n = 4 : num_list의 a번 인덱스부터 b번 인덱스까지 c 간격으로
	    		for(int i = a; i <= b; i+=c) {
	    			list.add(num_list[i]);
	    		}
	    		break;
    	}
    	
    	int[] answer = new int[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	
    	return answer;
    }
}
```







## 2.1. 첫번째로 나오는 음수

![image-20240724184342500](/images/2024-07-24-practice-programmers-12/image-20240724184342500.png)

## 2.2. 풀이



```java
class Solution {
    public int solution(int[] num_list) {
    	int answer = -1;
    	for(int i = 0; i < num_list.length; i++) {
    		if(num_list[i] < 0) {
    			answer = i;
    			break;
    		} 
    	}
    	return answer;
    }
}
```





## 3.1. 배열 만들기3

![image-20240724185142900](/images/2024-07-24-practice-programmers-12/image-20240724185142900.png)



## 3.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int[] arr, int[][] intervals) {
    	List<Integer> list = new ArrayList<Integer>();
    	while(intervals[0][0]<=intervals[0][1]) {
    		list.add(arr[intervals[0][0]++]);
    	}
    	while(intervals[1][0]<=intervals[1][1]) {
    		list.add(arr[intervals[1][0]++]);
    	}
    	int[] answer = new int[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	return answer;
    }
}
```





## 4.1. 2의 영역

![image-20240724190624771](/images/2024-07-24-practice-programmers-12/image-20240724190624771.png)



## 4.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int[] arr) {
    	List<Integer> list = new ArrayList<Integer>();
    	// 앞
    	boolean isFinded = false;
    	for(int i = 0; i < arr.length; i++) {
    		if(i == 0 && arr[i] != 2) continue;
    		if(arr[i] == 2) {
    			isFinded = true;
    		} 
    		if(isFinded) {
    			list.add(arr[i]);
    		}
    	}
    	
    	// 뒤
    	if(list.size() != 0) {
    		for(int i = list.size() - 1; i > 0; i--) {
    			if(list.get(i) == 2) {
    				break;
    			} else {
    				list.remove(i);
    			}
    		}
    	} else {
    		list.add(-1);
    	}
    	
    	int[] answer = new int[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	return answer;
    }
}
```



## 5.1. 배열 조각하기

![image-20240724193311641](/images/2024-07-24-practice-programmers-12/image-20240724193311641.png)



## 5.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[] solution(int[] arr, int[] query) {
    	// query배열의 인덱스(i)의 홀짝 여부에 따라 
    	// arr배열에서 query[i]번째 인덱스에 해당하는 요소의 
    	// 앞(홀수) 혹은 뒤(짝수)를 자르는 문제
    	
    	List<Integer> list = new ArrayList<Integer>();
    	for(int i = 0; i < arr.length; i++) {
    		list.add(arr[i]);
    	}
    	
    	for(int i = 0; i < query.length; i++) {
    		if(i % 2 == 0) {
    			for(int j = list.size()-1; j > query[i]; j--) {
    				list.remove(j);
    			}
    		} else {
    			for(int j = query[i]-1; j >= 0; j--) {
    				list.remove(j);
    			}
    		}
    	}
    	
    	int[] answer = new int[list.size()];
    	for(int i = 0; i < list.size(); i++) {
    		answer[i] = list.get(i);
    	}
    	
    	return answer;
    }
}
```



query[i]인덱스를 기준으로 앞뒤를 remove()메소드로 제거하려는 시도였는데, 처음에는 계속 실패했다.

그 원인을 찾아보니...



```java
...
		for(int i = 0; i < query.length; i++) {
    		if(i % 2 == 0) {
    			for(int j = list.size()-1; j > query[i]; j--) {
    				list.remove(j);
    			}
    		} else {
    			for(int j = query[i]-1; j >= 0; j--) {
    				list.remove(j);
    			}
    		}
    	} 
...
```

홀짝 여부에 따라 자를 부분이 앞 뒤인지를 판별하는 부분인데, else로 분기된 홀수의 경우에 문제가 있었다.



처음에는 조건이 다음과 같았다.

```java

        for(int j = 0; j < query[i]; j++) {
        	list.remove(j);
		}
```

위와 같은 코드에서 

arr: [1,2,3,4,5]

query: [4, 2] 의 경우,

arr: [2,3,4,5]

arr: [3,4,5] 와 같이 앞에서부터 값을 제거해나가도록 한 것인데, remove() 메소드를 통해 값을 제거하면, 인덱스가 하나씩 밀리게 되어 반복문이 가리키는 인덱스가 원래 의도한 값을 가리키지 사실을 간과한 것이다.



따라서 뒤에서부터 제거하는 코드로 수정한 후에 정상적으로 실행되는 것을 확인했다.

##  

> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
