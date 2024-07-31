---
layout: single
title:  "JSP 복습 (1)"
categories: study
tag: [자바, 스프링, JSP, MVC, 복습]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-07-30 18:45:31 +09:00
typora-root-url: ../
published: false
---



# 1. 목적

23년 11월 15일자 대덕인재개발원 JSP 강의 내용에 대한 복습이다. 과정을 잊지 않고 다음에 찾아보기 위해 기록하려 한다. 원래는 노션으로 정리한 그날의 실습 내용을 새로 프로젝트를 만들어서 반복 학습해볼 것이다.



# 2. 실습 - 준비

## 2.1. 프로젝트 생성 및 설정



![image-20240730201706676](/images/2024-07-30-review-spring-1/image-20240730201706676.png)





![image-20240730201805912](/images/2024-07-30-review-spring-1/image-20240730201805912.png)



![image-20240730201848809](/images/2024-07-30-review-spring-1/image-20240730201848809.png)



![image-20240730201938457](/images/2024-07-30-review-spring-1/image-20240730201938457.png)



![image-20240730201956453](/images/2024-07-30-review-spring-1/image-20240730201956453.png)



![image-20240730202046468](/images/2024-07-30-review-spring-1/image-20240730202046468.png)



![image-20240730202122491](/images/2024-07-30-review-spring-1/image-20240730202122491.png)



![image-20240730202159597](/images/2024-07-30-review-spring-1/image-20240730202159597.png)



## 2.2. pom.xml 설정



![image-20240730202351640](/images/2024-07-30-review-spring-1/image-20240730202351640.png)



![image-20240730202546059](/images/2024-07-30-review-spring-1/image-20240730202546059.png)



## 2.3. 라이브러리 추가

### 2.3.1. 라이브러리 추가 방법

[https://mvnrepository.com/](https://mvnrepository.com/)

![image-20240730202739205](/images/2024-07-30-review-spring-1/image-20240730202739205.png)

![image-20240730202757496](/images/2024-07-30-review-spring-1/image-20240730202757496.png)

![image-20240730202818019](/images/2024-07-30-review-spring-1/image-20240730202818019.png)



### 2.3.2. 라이브러리 추가

해당 복습 프로젝트에서는 방법만 숙지



## 2.4. 메이븐 빌드



![image-20240730203336622](/images/2024-07-30-review-spring-1/image-20240730203336622.png)



![image-20240730203411155](/images/2024-07-30-review-spring-1/image-20240730203411155.png)

![image-20240730203447319](/images/2024-07-30-review-spring-1/image-20240730203447319.png)



## 2.5. 인코딩 필터 등록



브라우저에서 보내는 요청(request)과 응답(response)을 모두 UTF-8로 고정하기 위해 인코딩 필터를 설정한다.



![image-20240730203712061](/images/2024-07-30-review-spring-1/image-20240730203712061.png)



```xml
	<filter>
		<filter-name>encodingFilter</filter-name>
		<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
		<init-param>
			<param-name>encoding</param-name>
			<param-value>UTF-8</param-value>
		</init-param>
		<init-param>
			<param-name>forceEncoding</param-name>
			<param-value>true</param-value>
		</init-param>
	</filter>	
	<filter-mapping>
		<filter-name>encodingFilter</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>
```





## 2.6. log4j 설정

root loger의 priority를 debug로 변경

개발시 디버그 용도로 사용한 메세지를 나타낸다.

![image-20240730204051804](/images/2024-07-30-review-spring-1/image-20240730204051804.png)



## 2.7. 템플릿 복사

강의 중 교수님이 제공하신 템플릿을 재사용한다.



![image-20240730204444673](/images/2024-07-30-review-spring-1/image-20240730204444673.png)



부트스트랩과 완성되지 않은 뷰들이다.



## 2.8. DB 계정 및 테이블 생성

미처 캡처하지 못해 강의 중 캡처했던 내용을 첨부함. 버전 및 일부 출력내용이 다를 수 있음

![image-20240730204713176](/images/2024-07-30-review-spring-1/image-20240730204713176.png)



![image-20240730204726861](/images/2024-07-30-review-spring-1/image-20240730204726861.png)



![image-20240730204741535](/images/2024-07-30-review-spring-1/image-20240730204741535.png)

![image-20240730205205900](/images/2024-07-30-review-spring-1/image-20240730205205900.png)





## 2.9. DB관련 라이브러리 pom.xml에 추가





![image-20240730205431902](/images/2024-07-30-review-spring-1/image-20240730205431902.png)

![image-20240730205945499](/images/2024-07-30-review-spring-1/image-20240730205945499.png)



## 2.10. root-context.xml 설정

![image-20240730210316895](/images/2024-07-30-review-spring-1/image-20240730210316895.png)

```XML

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd">
	
	<bean id="dataSource" class="org.apache.commons.dbcp2.BasicDataSource" destroy-method="close">
		<property name="driverClassName" value="oracle.jdbc.driver.OracleDriver"/>
		<property name="url" value="jdbc:oracle:thin:@localhost:1521:xe"/>
		<property name="username" value=""/>
		<property name="password" value=""/>
	</bean>
	
	<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
		<property name="dataSource" ref="dataSource"/>
		<property name="mapperLocations" value="classpath:/sqlmap/**/*_SQL.xml"/>
		<!-- <property name="configLocation" value="/WEB-INF/mybatisAlias/mybatisAlias.xml"/> -->
	</bean>
	
	<bean id="sqlSessionTemplate" class="org.mybatis.spring.SqlSessionTemplate">
		<constructor-arg index="0" ref="sqlSessionFactory"></constructor-arg>
	</bean>
	
</beans>
```



## 2.11. blank_SQL.xml 생성

마이바티스 매퍼 xml의 템플릿으로 사용할 파일을 생성

![image-20240730210725646](/images/2024-07-30-review-spring-1/image-20240730210725646.png)



### 2.11.1. dtd설정



[https://mybatis.org/mybatis-3/](https://mybatis.org/mybatis-3/)



![image-20240730211017708](/images/2024-07-30-review-spring-1/image-20240730211017708.png)



![image-20240730211123210](/images/2024-07-30-review-spring-1/image-20240730211123210.png)



```XML
<!DOCTYPE mapper
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
```



# 3. 실습 - 기능 구현

## 3.1. 기능

책 목록 조회, 상세 조회, 검색, 등록, 수정, 삭제



## 3.2. 패키지 구조

![image-20240730212433397](/images/2024-07-30-review-spring-1/image-20240730212433397.png)



## 3.2. 책 등록

### 3.2.1. BookInsertController.java

![image-20240730212626061](/images/2024-07-30-review-spring-1/image-20240730212626061.png)

@Controller 어노테이션이 있는 클래스는 스프링이 브라우저의 요청(request)을 받아들이는 컨트롤러라고 인지해서 자바 빈(Java Bean)으로 등록해서 관리한다.



![image-20240730212826753](/images/2024-07-30-review-spring-1/image-20240730212826753.png)

@RequestMapping  

- 요청 URL을 어떤 메소드가 처리할 지 여부를 결정 
- **클래스 라인**에 들어있다면 시작 URL을 처리  
- **메소드 라인**에 들어있다면 최종 목적이 URL을 처리

![image-20240730213225626](/images/2024-07-30-review-spring-1/image-20240730213225626.png)

![image-20240730213836334](/images/2024-07-30-review-spring-1/image-20240730213836334.png)

실행하자 아래와 같은 에러가 발생했다.

![image-20240730214014743](/images/2024-07-30-review-spring-1/image-20240730214014743.png)

메시지를 읽은 후 원인을 알 수 있었다.



![image-20240730214043053](/images/2024-07-30-review-spring-1/image-20240730214043053.png)



JSP가 views폴더 바로 아래에 존재했고, 컨트롤러에서의 설정과 일치하지 않아 찾지 못한 것이었다. 올바르게 설정하고 다시 실행해보았다.



![image-20240730214141619](/images/2024-07-30-review-spring-1/image-20240730214141619.png)

정상적으로 강의 때 제공받았던 템프릿 화면이 출력된다.



본격적인 등록은 다음에 진행할 것이다.





# 4. 용어

- Spring
- MVC
- WAS
- Maven
- Apache Tomcat

- mybatis / dtd
- pom.xml
- root-context.xml
- sqlSessionFactory, sqlSessionTemplete
- Bootstrap
- OracleDB
- 어노테이션
- Bean



