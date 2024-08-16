---
layout: single
title:  "프로그래머스 - 가장 많이 받은 선물"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-16 20:11:10 +09:00
typora-root-url: ../
---







# 1. 문제

## ![image-20240816193613726](/images/2024-08-16-practice-programmers-level1/image-20240816193613726.png)



# 2. 풀이

```java
import java.util.Arrays;

class Solution {
    public int solution(String[] friends, String[] gifts) {
		
    	String[][] giftsDimArr = new String[gifts.length][2];
    	int[][][] sendAndReceiveCnt3DArr = new int[friends.length][2][friends.length];
    	int[] pIdxArr = new int[friends.length];
    	int[] answer = new int[friends.length];
    	
    	// 선물 주고 받은 기록 3차원 배열로 저장하기
    	for(int i = 0; i < giftsDimArr.length; i++) {
    		giftsDimArr[i] = gifts[i].split(" ");
    	}
    	
        // 캐릭터 개개인이 다른 캐릭터와 주고 받은 숫자 배열로 저장하기
    	for(int i = 0; i < friends.length; i++) {
    		for(int j = 0; j < giftsDimArr.length; j++) {
    			if(giftsDimArr[j][0].equals(friends[i])) {
    				for(int k = 0; k < friends.length; k++) {
    					if(giftsDimArr[j][1].equals(friends[k])) {
    						sendAndReceiveCnt3DArr[i][0][k]++;
    					}
    				}
    			}
    			
    			if(giftsDimArr[j][1].equals(friends[i])) {
    				for(int k = 0; k < friends.length; k++) {
    					if(giftsDimArr[j][0].equals(friends[k])) {
    						sendAndReceiveCnt3DArr[i][1][k]++;
    					}
    				}
    			}
    		}
    	}
    	
        // sendAndReceiveCnt3DArr[i][0][j] (== / > / < ) sendAndReceiveCnt3DArr[i][1][j]
        // [i]<-인덱스 캐릭터 [0/1]<-주기 or 받기 [j]<-주고 받는 캐릭터
    	
    	// 선물지수 계산
    	for(int i = 0; i < friends.length; i++) {
    		int sum = 0;
    		for(int j = 0; j < sendAndReceiveCnt3DArr[i][0].length; j++) {
    			sum += sendAndReceiveCnt3DArr[i][0][j] - sendAndReceiveCnt3DArr[i][1][j];
    		}
    		
    		pIdxArr[i] = sum;
    	}
        				
        // 선물 결산
    	for(int i = 0; i < friends.length; i++) {
    		for(int j = 0; j < friends.length; j++) {
    			if(j < i || friends[i].equals(friends[j])) continue;
				int send = sendAndReceiveCnt3DArr[i][0][j];
				int receive = sendAndReceiveCnt3DArr[i][1][j];

				if(send == receive) {
					if(pIdxArr[i] > pIdxArr[j]) {
						answer[i]++;
					} else if(pIdxArr[i] < pIdxArr[j]) {
						answer[j]++;
					}
				} else {
					if(send > receive) {
						answer[i]++;
					} else {
						answer[j]++;
					}
				}
    			
    		}
    	}
    	
    	Arrays.sort(answer);
		return answer[answer.length-1];	// 가장 큰 값 반환
	}
}
```





먼저 문제를 풀기 전에 개인적으로 알아볼 수 있게 정리를 해보았다.

두 사람이 선물을 주고 받은 기록 중 어느 하나가 많다면..
  더 많이 준 사람이 선물을 하나 받는다. +1

두 사람이 선물을 주고 받은 기록이 하나도 없거나 같다면...
  주고 받은 기록이 하나도 없거나 같다면...
    마찬가지로 선물 지수가 높은 사람이 하나 받는다. +1
  선물지수가 같다면 주고 받지 않는다. +0



문제를 3차원 배열로 푼 이유는 다른 방법이 바로 생각나지 않았기 때문인데, 결과적으로는 복잡한 코드로 이어졌다.



```java
	// 선물 주고 받은 기록 3차원 배열로 저장하기
	for(int i = 0; i < giftsDimArr.length; i++) {
		giftsDimArr[i] = gifts[i].split(" ");
	}
```

우선 선물을 주고 받은 기록을 담은 배열인 gifts를 split()함수를 사용해 2차원 배열로 만들었다. 이는 선물을 **주는 사람**과 **받는 사람**을 구분하기 위함이었다.



```java
        // 캐릭터 개개인이 다른 캐릭터와 주고 받은 숫자 배열로 저장하기
    	for(int i = 0; i < friends.length; i++) {
    		for(int j = 0; j < giftsDimArr.length; j++) {
    			if(giftsDimArr[j][0].equals(friends[i])) {
    				for(int k = 0; k < friends.length; k++) {
    					if(giftsDimArr[j][1].equals(friends[k])) {
    						sendAndReceiveCnt3DArr[i][0][k]++;
    					}
    				}
    			}
    			
    			if(giftsDimArr[j][1].equals(friends[i])) {
    				for(int k = 0; k < friends.length; k++) {
    					if(giftsDimArr[j][0].equals(friends[k])) {
    						sendAndReceiveCnt3DArr[i][1][k]++;
    					}
    				}
    			}
    		}
    	}
```



다음으로는 캐릭터 개개인이 다른 캐릭터와 선물을 몇개씩 주고 받았는지 저장하기 위해 3차원배열을 이용하였다.

[ [[0, 0, 2, 0], [0, 3, 1, 1]], [[3, 0, 0, 0], [0, 0, 1, 0]], [[1, 1, 0, 0],[2, 0, 0, 0]], [[1, 0, 0, 0],[0, 0, 0, 0]] ]

여기서 [0, 0, 2, 0]는 muzi가 ryan, frodo, neo에게 선물을 준 횟수, [0, 3, 1, 1]는 muzi가 ryan, frodo, neo에게 선물을 받은 횟수이다.



그 뒤로 선물 지수를 계산했는데, 

```java
	// sendAndReceiveCnt3DArr[i][0][j] (== / > / < ) sendAndReceiveCnt3DArr[i][1][j]
	// [i]<-인덱스 캐릭터 [0/1]<-주기 or 받기 [j]<-주고 받는 캐릭터
	
    // 선물지수 계산
    for(int i = 0; i < friends.length; i++) {
        int sum = 0;
        for(int j = 0; j < sendAndReceiveCnt3DArr[i][0].length; j++) {
            sum += sendAndReceiveCnt3DArr[i][0][j] - sendAndReceiveCnt3DArr[i][1][j];
        }

        pIdxArr[i] = sum;
    }
```

[0, 0, 2, 0]의 합 2와 [0, 3, 1, 1]의 합 5를 뺀 -3이 muzi의 선물지수가 된다.



```java
        // 선물 결산
    	for(int i = 0; i < friends.length; i++) {
    		for(int j = 0; j < friends.length; j++) {
    			if(j < i || friends[i].equals(friends[j])) continue;
				int send = sendAndReceiveCnt3DArr[i][0][j];
				int receive = sendAndReceiveCnt3DArr[i][1][j];

				if(send == receive) {
					if(pIdxArr[i] > pIdxArr[j]) {
						answer[i]++;
					} else if(pIdxArr[i] < pIdxArr[j]) {
						answer[j]++;
					}
				} else {
					if(send > receive) {
						answer[i]++;
					} else {
						answer[j]++;
					}
				}
    			
    		}
    	}
```



다음으로 선물을 결산하는 부분이다.

선물을 주고 받는 것이므로

muzi와 ryan가 주고 받은 선물
muzi와 frodo가 주고 받은 선물
muzi와 neo가 주고 받은 선물
ryan와 frodo가 주고 받은 선물
ryan와 neo가 주고 받은 선물
frodo와 neo가 주고 받은 선물

을 비교하여야한다. 따라서 이중 for문의 j가 i보다 큰 경우(중복 방지)와, 본인이 본인과 주고받는 경우는 continue하도록 하였다.



```java
    	Arrays.sort(answer);
		return answer[answer.length-1];	// 가장 큰 값 반환
```



처음에 정리한 대로 조건 분기를 주어 answer배열에 각 캐릭터가 **다음 달 받게 되는 선물의 갯수**를 저장하고, 가장 큰 값을 return하도록 하였다.



# 3. 마치며

처음에 3차원 배열을 선택한 것과, 중간에 오기가 생겨서 끝까지 코딩한 것이 이런 복잡한 결과로 이어졌다. 모로 가도 서울만 가면 된다고 어떻게든 실행만 되게만 하자는 마음으로 일단 문제를 해결할 수는 있었다. 그러나, 유지보수에 있어서 다른 개발자가 이런 코드를 보았을 때, 쉽게 이해할 수 있을 것이라는 생각은 들지 않았다.  또 성능적으로도 더 좋은 방법을 떠올릴 수 있었을 것 같다는 생각이 든다.



지금 당장에 바로 다른 방법이 떠오르지 않은 것은 기존의 코딩하던 방식을 잘 바꾸지 않기 때문이라고 생각한다. 아마 익숙한 방법을 빠르게 선택해서 실행될 때까지 시도해보는게 습관이 되어서 그런 것 같다. 이러한 점은 반성해야할 부분이다. 문제를 해결했다고 넘어가지 말고 다른 개발자들의 풀이를 보고 더 효율적인 방법이 있다면 새로운 방법을 사용해보는 습관을 들여야겠다.







> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
