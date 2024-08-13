---
layout: single
title:  "프로그래머스 코딩 기초 트레이닝 일일과제 25일차 풀이"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-13 20:26:39 +09:00
typora-root-url: ../
---







# 1. 문제



## 1.1. 정수를 나선형으로 배치하기

![image-20240812202151959](/images/2024-08-12-practice-programmers-25/image-20240812202151959.png)

## 1.2. 풀이

```java
class Solution {
    public int[][] solution(int n) {
    	int[][] answer = new int[n][n];
    	int count = 1;
    	int row = 0;
    	int col = 0;
    	
    	// 오른쪽, 아래, 왼쪽, 위로 한번씩 순회 후에는 순회할 길이가 2씩 작아진다.
    	for(int i = n; i > 0; i -= 2) {
            
    		// 오른쪽
    		for(int j = 0; j < i; j++) {
    			answer[row][col++] += count++;
    		}
    		
    		// 마지막 실행 후 증가하는 열을 다시 감소하고 아래로 이동을 위해 다음 행으로 진행한다.
    		col--;
    		row++;
    		
            // 아래
    		for(int j = 0; j < i - 1; j++) {
    			answer[row++][col] += count++;
    		}
    		
            // 마지막 실행 후 증가하는 행을 다시 감소하고 왼쪽으로 이동을 위해 전 열로 진행한다.
    		row--;
    		col--;
    		
    		// 왼쪽
    		for(int j = 0; j < i - 1; j++) {
    			answer[row][col--] += count++;
    		}
    		
            // 마지막 실행 후 감소하는 열을 다시 증가시키고 위로 이동을 위해 전 행으로 진행한다.
    		col++;
    		row--;
    		
    		// 위로
    		for(int j = 0; j < i - 2; j++) {
    			answer[row--][col] += count++;
    		}
            
            // 마지막 실행 후 감소하는 행을 다시 증가시키고 다음 순환을 위해 다음 열로 진행한다.
    		row++;
    		col++;
    		
    	}
    	
    	return answer;
	}
}
```



### 1.3. 참고

- [https://hihiha2.tistory.com/112](https://hihiha2.tistory.com/112)





## 2.1. 특별한 2차원 배열

![image-20240812202218249](/images/2024-08-12-practice-programmers-25/image-20240812202218249.png)





## 2.2. 풀이

```java
class Solution {
    public int solution(int[][] arr) {
    	int answer = 0;
    	boolean miss = false;
    	for(int i = 0; i < arr.length; i++) {
    		for(int j = 0; j < arr[i].length; j++) {
				if(arr[i][j] == arr[j][i]) {
					answer = 1;
				} else {
					miss = true;
				}
    		}
    	}
    	
    	if(miss) {
    		answer = 0;
    	}
    	return answer;
	}
}
```







## 3.1. 정사각형으로 만들기

![image-20240812202248643](/images/2024-08-12-practice-programmers-25/image-20240812202248643.png)



## 3.2. 풀이

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public int[][] solution(int[][] arr) {
    	List<List<Integer>> list = new ArrayList<List<Integer>>();
    	List<Integer> inList;
    	int row = arr.length;
    	int column = arr[0].length;
    	
    	for(int i = 0; i < row; i++) {
    		
			inList = new ArrayList<Integer>();
			
			// 열(column) 구성
    		for(int j = 0; j < arr[i].length; j++) {
    			inList.add(arr[i][j]);
    		}
    		
    		// 행이 열보다 크다면...
    		if(row > column) {
    			// 해당 열에 0을 행의 수 만큼 추가
    			for(int k = 0; k < row - column; k++) {
    				inList.add(0);
    			}
    		}
    		
    		// 열을 리스트에 추가
    		list.add(inList);
    	}
    	
    	// 루프를 벗어난 후 (열 추가가 끝난 후) 열이 행보다 크다면, 0으로 이루어진 행을 열 크기 만큼 추가
    	if(column > row) {
    		for(int j = 0; j < column - row; j++) {
    			inList = new ArrayList<Integer>();
    			
    			for(int k = 0; k < list.get(0).size(); k++) {
    				inList.add(0);
    			}
    			
    			list.add(inList);
    		}
    	}
    	
    	// 리스트 이차원 배열 변환 과정
    	int[][] answer = new int[list.size()][list.get(0).size()];
    	for(int i = 0; i < list.size(); i++) {
    		for(int j = 0; j < list.get(0).size(); j++) {
    			answer[i][j] = list.get(i).get(j);
    		}
    	}
    	return answer;
	}
}
```





## 4.1. 이차원 배열 대각선 순회하기

![image-20240813192016810](/images/2024-08-13-practice-programmers-25/image-20240813192016810.png)



## 4.2. 풀이

```java
class Solution {
    public int solution(int[][] board, int k) {
    	int sum = 0;
    	for(int i = 0; i < board.length; i++) {
    		for(int j = 0; j < board[i].length; j++) {
    			if(i + j <= k) {
    				sum += board[i][j];
    			}
    		}
    	}
    	return sum;
	}
}
```





> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
