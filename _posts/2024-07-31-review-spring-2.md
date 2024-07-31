---
layout: single
title:  "JSP 복습 (2)"
categories: study
tag: [자바, 스프링, JSP, MVC, 복습]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-31 23:01:47 +09:00
typora-root-url: ../
published: false
---



# 1. 목적

대덕인재개발원 JSP 강의 내용에 대한 복습이다. 전 포스팅에서 이어진다.



# 2. 실습

## 2.1. 책 등록하기



### 2.1.1. 템플릿 form 요청부 수정

![image-20240730214743116](/images/2024-07-30-review-spring-2/image-20240730214743116.png)



### 2.1.2. 컨트롤러 작성

**BookInsertController.java**

![image-20240730215756215](/images/2024-07-30-review-spring-2/image-20240730215756215.png)

![image-20240730215904914](/images/2024-07-30-review-spring-2/image-20240730215904914.png)

**@Inject 의존성 주입**



### 2.1.3. 서비스 인터페이스, 구현체 클래스

![image-20240730215934457](/images/2024-07-30-review-spring-2/image-20240730215934457.png)



인터페이스의 추상 메소드는 직접 입력하기보단 컨트롤러에서 해당 메소드가 존재하지 않을 때 발생하는 오류를 이용해 자동으로 생성했다.



### 2.1.4. 매퍼 xml 작성



![image-20240730220112564](/images/2024-07-30-review-spring-2/image-20240730220112564.png)



구현체 클래스 BookServiceImpl은 클래스 생성 시 구현할 인터페이스를 선택하여 생성했다.

이렇게 하면 재정의할 메소드들을 자동으로 선언할 수 있다.



![image-20240730221445850](/images/2024-07-30-review-spring-2/image-20240730221445850.png)

서비스 구현체 클래스에 의존성을 주입해주고 DAO 또한 마찬가지로 생성했다.



컨트롤러 작성 - 서비스 의존성 주입 - 서비스 / 구현체 클래스 작성  - DAO 의존성 주입 - DAO 작성 순으로 진행했다.





![image-20240730221820427](/images/2024-07-30-review-spring-2/image-20240730221820427.png)

DAO에서는 @Repository 어노테이션으로 DAO가 DB와 통신하는 클래스임을 스프링에 알렸다.



![image-20240730222930616](/images/2024-07-30-review-spring-2/image-20240730222930616.png)

book_SQL.xml 매퍼를 만들어 쿼리를 작성했다. 마이바티스를 통해 쿼리를 xml로 간편하게 작성할 수 있었다. 



위에서 book_id는 시퀀스로 증가시키고 나머지 필드는 매핑된 Map에서 받아온 패러미터를 플레이스홀더에 바인딩 하도록 했다.

#{}는 인젝션 공격에 강하다고 하는 데, 다음에 알아보아야겠다.



### 2.1.5. 실행

![image-20240731213803952](/images/2024-07-30-review-spring-2/image-20240731213803952.png)

![image-20240731213748390](/images/2024-07-30-review-spring-2/image-20240731213748390.png)

![image-20240731213826972](/images/2024-07-30-review-spring-2/image-20240731213826972.png)

요청 주소가 틀렸다.





![image-20240731213904626](/images/2024-07-30-review-spring-2/image-20240731213904626.png)

form.jsp파일의 form태그의 action속성을 수정해주었다.



![image-20240731214023283](/images/2024-07-30-review-spring-2/image-20240731214023283.png)

컨트롤러에 클래스 레벨에 /book으로 매핑시켜주었기 때문에...

![image-20240731214121499](/images/2024-07-30-review-spring-2/image-20240731214121499.png)

이번에는 등록 될까?

![image-20240731214305062](/images/2024-07-30-review-spring-2/image-20240731214305062.png)



안 됐다.

```
심각: 경로 []의 컨텍스트 내의 서블릿 [appServlet]을(를) 위한 Servlet.service() 호출이, 근본 원인(root cause)과 함께, 예외 [Request processing failed; nested exception is org.mybatis.spring.MyBatisSystemException: nested exception is org.apache.ibatis.type.TypeException: Could not set parameters for mapping: ParameterMapping{property='bookId', mode=IN, javaType=class java.lang.Object, jdbcType=null, numericScale=null, resultMapId='null', jdbcTypeName='null', expression='null'}. Cause: org.apache.ibatis.type.TypeException: Error setting null for parameter #1 with JdbcType OTHER . Try setting a different JdbcType for this parameter or a different jdbcTypeForNull configuration property. Cause: java.sql.SQLException: 부적합한 열 유형: 1111]을(를) 발생시켰습니다.
java.sql.SQLException: 부적합한 열 유형: 1111
```



![image-20240731214559916](/images/2024-07-30-review-spring-2/image-20240731214559916.png)

DAO에 네임스페이스가 누락됐었다.

![image-20240731214637182](/images/2024-07-30-review-spring-2/image-20240731214637182.png)

![image-20240731214833343](/images/2024-07-30-review-spring-2/image-20240731214833343.png)

여전히 에러!





```
심각: 경로 []의 컨텍스트 내의 서블릿 [appServlet]을(를) 위한 Servlet.service() 호출이, 근본 원인(root cause)과 함께, 예외 [Request processing failed; nested exception is org.mybatis.spring.MyBatisSystemException: nested exception is org.apache.ibatis.type.TypeException: Could not set parameters for mapping: ParameterMapping{property='bookId', mode=IN, javaType=class java.lang.Object, jdbcType=null, numericScale=null, resultMapId='null', jdbcTypeName='null', expression='null'}. Cause: org.apache.ibatis.type.TypeException: Error setting null for parameter #1 with JdbcType OTHER . Try setting a different JdbcType for this parameter or a different jdbcTypeForNull configuration property. Cause: java.sql.SQLException: 부적합한 열 유형: 1111]을(를) 발생시켰습니다.
java.sql.SQLException: 부적합한 열 유형: 1111
```



Could not set parameters for mapping 파라미터를 매핑하지 못했다고 한다.

bookId... 아무래도 카멜케이스에 너무 익숙해져버린데다가 프로젝트를 진행하며 자주 사용하다보니 머리를 거치지 않고 그대로 적어버린 것 같다.



다음부터는 잘 보고 적어야지



![image-20240731215229260](/images/2024-07-30-review-spring-2/image-20240731215229260.png)



![image-20240731215344502](/images/2024-07-30-review-spring-2/image-20240731215344502.png)



![image-20240731215706525](/images/2024-07-30-review-spring-2/image-20240731215706525.png)

ServiceImpl도 수정



![image-20240731215816074](/images/2024-07-30-review-spring-2/image-20240731215816074.png)

![image-20240731215907014](/images/2024-07-30-review-spring-2/image-20240731215907014.png)

성공했다.

아직 detail페이지를 연결하지 않았으니 에러가 뜨는 것은 당연하다.

![image-20240731220026088](/images/2024-07-30-review-spring-2/image-20240731220026088.png)



