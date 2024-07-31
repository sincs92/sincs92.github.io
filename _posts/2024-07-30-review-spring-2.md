---
layout: single
title:  "JSP 복습 (2)"
categories: study
tag: [자바, 스프링, JSP, MVC, 복습]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-30 18:45:31 +09:00
typora-root-url: ../
publised: false
---



# 1. 목적

23년 11월 16일자 대덕인재개발원 JSP 강의 내용에 대한 복습이다. 전 포스팅에서 이어진다.



# 2. 실습

## 2.1. 책 등록하기



![image-20240730214743116](/images/2024-07-30-review-spring-2/image-20240730214743116.png)



BookInsertController.java

![image-20240730215756215](/images/2024-07-30-review-spring-2/image-20240730215756215.png)

![image-20240730215904914](/images/2024-07-30-review-spring-2/image-20240730215904914.png)

@Inject 의존성 주입



![image-20240730215934457](/images/2024-07-30-review-spring-2/image-20240730215934457.png)

인터페이스의 추상메소드는 직접 입력하기보단 컨트롤러에서 해당 메소드가 존재하지 않을 때 발생하는 오류를 이용해 자동으로 생성했다.



![image-20240730220112564](/images/2024-07-30-review-spring-2/image-20240730220112564.png)



구현체 클래스 BookServiceImpl은 class생성 시 구현할 인터페이스를 선택하여 생성했다.



![image-20240730221445850](/images/2024-07-30-review-spring-2/image-20240730221445850.png)

서비스 구현체 클래스에 의존성을 주입해주고 DAO도 생성했다.



![image-20240730221820427](/images/2024-07-30-review-spring-2/image-20240730221820427.png)

@Repository 어노테이션으로 DAO가 DB와 통신하는 클래스임을 스프링에 알렸다.



![image-20240730222930616](/images/2024-07-30-review-spring-2/image-20240730222930616.png)

book_SQL.xml 매퍼를 만들어 쿼리를 작성했다. 마이바티스를 통해 쿼리를 xml로 간편하게 작성할 수 있었다. 위위에서 book_id는 시퀀스로 증가시키고 나머지 필드는 매핑된 Map에서 받아온 패러미터를 플레이스홀더에 바인딩 하고 있다.



아직 detail.jsp나 
