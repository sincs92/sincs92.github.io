---
layout: single
title:  "JSP 복습 (3)"
categories: study
tag: [자바, 스프링, JSP, MVC, 복습]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-31 23:01:47 +09:00
typora-root-url: ../
published: false
---



# 1. 서론

앞선 포스팅에서는 책을 등록하는 부분까지 했었다. 이제 상세 조회 페이지를 연결하여 책의 정보를 출력할 차례이다.



# 2. 실습

## 2.1. 상세정보 보기

### 2.1.1. Controller

![image-20240801224445297](/images/2024-08-01-review-spring-3/image-20240801224445297.png)



### 2.1.2. ServiceImpl

![image-20240801224509791](/images/2024-08-01-review-spring-3/image-20240801224509791.png)



### 2.1.3. DAO

![image-20240801224539989](/images/2024-08-01-review-spring-3/image-20240801224539989.png)



### 2.1.4. 매퍼 XML

![image-20240801224612365](/images/2024-08-01-review-spring-3/image-20240801224612365.png)



### 2.1.6. JSP

![image-20240801224842609](/images/2024-08-01-review-spring-3/image-20240801224842609.png)

컨트롤러에서 addObject로 전달한 Map객체를 키를 이용해 값을 가져오고 있음



### 2.1.7. 실행

![image-20240801224644902](/images/2024-08-01-review-spring-3/image-20240801224644902.png)

처음 시도에는 값이 뜨지 않았는데, 그 이유를 살펴보니, 이전 강의 내용 중에도 실수했던 내용이 있었다.



![image-20240801225646428](/images/2024-08-01-review-spring-3/image-20240801225646428.png)

![image-20240801225708176](/images/2024-08-01-review-spring-3/image-20240801225708176.png)

![image-20240801225728308](/images/2024-08-01-review-spring-3/image-20240801225728308.png)



Mybatis에서 resultType을 VO가 아닌 HashMap으로 주게 되면 키가 대문자로 들어가게 된다는 사실을 또 한번 상기하게 되었다. (오라클의 경우. 다른 DB면 다를 수도 있다고 한다.)





## 2.2. 책 수정하기

