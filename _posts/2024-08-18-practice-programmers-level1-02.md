---
layout: single
title:  "프로그래머스 - [PCCP 기출문제] 1번 / 붕대 감기"
categories: study
tag: [자바, 프로그래머스, 코딩 테스트]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-18 20:44:03 +09:00
typora-root-url: ../
---







# 1. 문제

![image-20240818203020306](/images/2024-08-16-practice-programmers-level1-02/image-20240818203020306.png)

![image-20240818203038301](/images/2024-08-16-practice-programmers-level1-02/image-20240818203038301.png)



# 2. 풀이

{% raw %}

```java
class Solution {
    public int solution(int[] bandage, int health, int[][] attacks) {
    	int bandageCnt = 0;				// 붕대 감기 카운트
    	int currentHealth = health;		// 현재 체력
    	
    	// 마지막으로 공격 받은 시간까지 1초씩 증가
    	for(int time = 0; time <= attacks[attacks.length-1][0]; time++) {
    		boolean attacked = false;
    		// 공격 받은 경우, 공격 플래그를 true로 전환하고, 현재 체력에서 데미지를 입은 만큼 경감한다.
    		// 현재 체력이 0보다 작거나 0인 경우, 즉시 사망 처리하고 -1을 리턴한다.
    		for(int i = 0; i < attacks.length; i++) {
    			if(time == attacks[i][0]) {
    				currentHealth -= attacks[i][1];
    				if(currentHealth <= 0) return -1;
    				
    				bandageCnt = 0;
    				attacked = true;
    			}
    		}
    		
    		// 공격 받지 않은 경우 붕대 감기를 시전한다.
			if(!attacked) {
				bandageCnt++;
				
				// 회복된 체력은 최대 체력보다 높을 수 없다.
				if(currentHealth + bandage[1] > health) {
					currentHealth = health;
				} else {
					currentHealth += bandage[1];
					
					// 연속 회복 횟수가 bandage[0]에 도달하면 회복 보너스를 받는데, 
					// 이 역시 최대 체력을 초과할 수 없다.
					if(bandageCnt == bandage[0]) {
						currentHealth = currentHealth + bandage[2] > health ? health : currentHealth + bandage[2]; 
						
						// 회복 보너스를 받고 나면 시전 횟수는 초기화 된다.
						bandageCnt = 0;
					}
				}
			} else {
				attacked = false;
			}
			
    	}
    	
    	return currentHealth;
	}
}
```





우선 문제를 내가 알아보기 편하게 정리했다.

```java
    	/*
			bandage = {5, 1, 5} 
					시전시간, 회복량, 연속회복 보너스
			attacks = {{2, 10}, {9, 15}, {10, 5}, {11, 5}}
			        시전시간 피해량

			붕대 감기는 bandage[0]초 동안 붕대를 감으면서 1초마다 bandage[1]만큼의 체력을 회복한다
			bandage[0]초 연속으로 붕대를 감는 데 성공한다면 bandage[2]만큼의 체력을 추가로 회복한다.
			현재 체력이 최대 체력(health)보다 커지는 것은 불가능하다.
						
			몬스터에게 공격을 당하면 기술(붕대감기)이 취소. (연속보너스 x) 
			공격을 당하는 순간에는 체력을 회복할 수 없음. 
			몬스터에게 공격당해 기술이 취소 or 기술이 끝나면 그 즉시 붕대 감기를 다시 사용.
			연속 성공 시간이 0으로 초기화됩니다.
			몬스터의 공격을 받으면 정해진 피해량만큼 현재 체력이 줄어듭니다.
			이때, 현재 체력이 0 이하가 되면 캐릭터가 죽으며 더 이상 체력을 회복할 수 없다.
			모든 공격이 끝난 직후 남은 체력을 return. 
			만약 몬스터의 공격을 받고 캐릭터의 체력이 0 이하가 되어 죽는다면 -1을 return
    	 */
```

다시 요약하자면

**모든 공격이 끝날 때까지** 1초씩 증가하며, **피격**을 당하지 않으면 붕대 감기를 시전할 수 있고, 피격을 당하게 되면 체력이 감소하면서 **붕대 감기 횟수가 초기화** 된다. **체력이 0 이하가 되면 사망**한다. 붕대 감기를 시전할 때 피격당하지 않고 bandage[1]만큼의 회복을 bandage[0]초 연속 시전하게 되면 bandage[2]의 **보너스**를 받는다. 이 역시 **붕대 감기 횟수가 초기화** 된다.



```java
    	for(int time = 0; time <= attacks[attacks.length-1][0]; time++) {
        	...
        }
```



먼저 시간의 흐름을 구현하기 위해, 마지막 공격인 ```attacks[attacks.length-1][0]```초 까지 time을 1초씩 증가시키도록 했다.



```java
    		boolean attacked = false;
    		// 공격 받은 경우, 공격 플래그를 true로 전환하고, 현재 체력에서 데미지를 입은 만큼 경감한다.
    		// 현재 체력이 0보다 작거나 0인 경우, 즉시 사망 처리하고 -1을 리턴한다.
    		for(int i = 0; i < attacks.length; i++) {
    			if(time == attacks[i][0]) {
    				currentHealth -= attacks[i][1];
    				if(currentHealth <= 0) return -1;
    				
    				bandageCnt = 0;
    				attacked = true;
    			}
    		}
```

시간이 공격 받는 타이밍과 일치하는 경우, 붕대 감기 시전은 불가하고, 데미지에 따라 현재 체력이 감소한다.

체력이 0 이하가 되면 사망하기 때문에 -1을 리턴한다.

공격을 받았으므로 붕대감기 연속 횟수는 초기화 되고, 피격 여부를 판단하는 attacked 플래그를 true로 전환한다.



```java
    		// 공격 받지 않은 경우 붕대 감기를 시전한다.
			if(!attacked) {
				bandageCnt++;
				
				// 회복된 체력은 최대 체력보다 높을 수 없다.
				if(currentHealth + bandage[1] > health) {
					currentHealth = health;
				} else {
					currentHealth += bandage[1];
					
					// 연속 회복 횟수가 bandage[0]에 도달하면 회복 보너스를 받는데, 
					// 이 역시 최대 체력을 초과할 수 없다.
					if(bandageCnt == bandage[0]) {
						currentHealth = currentHealth + bandage[2] > health ? health : currentHealth + bandage[2]; 
						
						// 회복 보너스를 받고 나면 시전 횟수는 초기화 된다.
						bandageCnt = 0;
					}
				}
			} else {
				attacked = false;
			}
```

최대 체력을 초과해 회복할 수 없음을 유의하며, 붕대감기 시전을 구현했다.

붕대감기 횟수를 초기화하고, 피격 여부를 판단하는 플래그를 다시 false로 되돌려주어 다음 반복에서 사용하도록 하였다.



{% endraw %}

> 문제 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
