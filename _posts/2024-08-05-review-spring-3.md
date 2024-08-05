---
layout: single
title:  "JSP 복습 (3)"
categories: study
tag: [자바, 스프링, JSP, MVC, 복습]
author_profile: true
sidebar:
    nav: "docs"
date: 2024-08-05 23:23:51 +09:00
typora-root-url: ../

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



Mybatis에서 resultType을 VO가 아닌 HashMap으로 주게 되면 키가 대문자로 들어가게 된다. 이는 오라클의 경우이고 다른 DB면 다를 수도 있다고 한다.





## 2.2. 책 수정하기

### 2.2.1. Detail.jsp 수정

![image-20240805213539008](/images/2024-08-01-review-spring-3/image-20240805213539008.png)

수정 버튼을 눌렀을 시, GET요청 하도록 href를 설정해주고, 파라미터로 bookId를 보내도록 했다. 이 bookId는 상세 페이지로 이동할 때 모델에 담아왔던 값이다.



### 2.2.2. Controller

![image-20240805214210134](/images/2024-08-01-review-spring-3/image-20240805214210134.png)

컨트롤러에 GET요청에 대해 매핑될 메서드를 작성해주고, 폼 양식 페이지로 이동할 때, bookId를 이용해 책의 정보를 다시 조회하여 뷰에 전달하도록 하였다.



![image-20240805214537424](/images/2024-08-01-review-spring-3/image-20240805214537424.png)

폼 양식 페이지에 모델에서 받아온 값을 el태그를 이용해 바인딩하고, 유저가 자신이 입력한 값을 수정하기 전에 확인할 수 있도록 하였다.



### 2.2.3. update.jsp (수정 폼) 수정

![image-20240805214649858](/images/2024-08-01-review-spring-3/image-20240805214649858.png)



폼 태그를 이용해 수정 양식을 POST로 요청할 때, bookId도 함께 전송하도록 hidden태그를 이용했다.



### 2.2.4. Controller(POST)

![image-20240805214755237](/images/2024-08-01-review-spring-3/image-20240805214755237.png)



수정에 성공하면 다시 해당 책의 상세페이지로 이동, 실패하면 폼 양식 페이지로 다시 이동하도록 했다.



### 2.2.5. Service, ServiceImpl

![image-20240805214910948](/images/2024-08-01-review-spring-3/image-20240805214910948.png)



### 2.2.6. DAO

![image-20240805214924241](/images/2024-08-01-review-spring-3/image-20240805214924241.png)



### 2.2.7. MapperXml

![image-20240805214951537](/images/2024-08-01-review-spring-3/image-20240805214951537.png)





### 2.2.8. 실행

![image-20240805215356748](/images/2024-08-01-review-spring-3/image-20240805215356748.png)



![image-20240805215410212](/images/2024-08-01-review-spring-3/image-20240805215410212.png)



![image-20240805215426734](/images/2024-08-01-review-spring-3/image-20240805215426734.png)

![image-20240805215438288](/images/2024-08-01-review-spring-3/image-20240805215438288.png)

## 2.3. 책 삭제하기

### 2.3.1. 삭제 확인

![image-20240805223932934](/images/2024-08-05-review-spring-3/image-20240805223932934.png)

![image-20240805224024012](/images/2024-08-05-review-spring-3/image-20240805224024012.png)

제이쿼리 임포트 후 삭제 버튼 액션에 대한 코드 작성



### 2.3.2. Controller

![image-20240805224321956](/images/2024-08-05-review-spring-3/image-20240805224321956.png)

### 2.3.3. ServiceImpl

![image-20240805224406519](/images/2024-08-05-review-spring-3/image-20240805224406519.png)

### 2.3.4. DAO

![image-20240805224458162](/images/2024-08-05-review-spring-3/image-20240805224458162.png)

### 2.3.5. 매퍼XML

![image-20240805224523865](/images/2024-08-05-review-spring-3/image-20240805224523865.png)





실행결과를 보기 위해서는 list페이지를 작성해야한다.





## 2.4. 책 목록 조회

### 2.4.1. jstl 태그 라이브러리

![image-20240805225229832](/images/2024-08-05-review-spring-3/image-20240805225229832.png)

반복문 사용을 위한 태그 라이브러리 설정



![image-20240805225521085](/images/2024-08-05-review-spring-3/image-20240805225521085.png)

책 목록을 List로 받아올 것이기 때문에, 위와 같이 설정해주었다.



### 2.4.2. Controller

![image-20240805225602362](/images/2024-08-05-review-spring-3/image-20240805225602362.png)



### 2.4.3. ServiceImpl

![image-20240805225651173](/images/2024-08-05-review-spring-3/image-20240805225651173.png)

### 2.4.4. DAO

![image-20240805225704485](/images/2024-08-05-review-spring-3/image-20240805225704485.png)

### 2.4.5. 매퍼xml

![image-20240805225715662](/images/2024-08-05-review-spring-3/image-20240805225715662.png)



### 2.4.6. 실행

![image-20240805225738599](/images/2024-08-05-review-spring-3/image-20240805225738599.png)



## 2.5. 검색

### 2.5.1. Controller

![image-20240805231928466](/images/2024-08-05-review-spring-3/image-20240805231928466.png)



검색을 위해 키워드를 사용하기 위해 메서드의 패러미터를 map을 받아오도록 수정했다.



### 2.5.2. ServiceImpl

![image-20240805232101272](/images/2024-08-05-review-spring-3/image-20240805232101272.png)

### 2.5.3. DAO

![image-20240805232213828](/images/2024-08-05-review-spring-3/image-20240805232213828.png)

### 2.5.4. 매퍼xml

![image-20240805232237313](/images/2024-08-05-review-spring-3/image-20240805232237313.png)



### 2.5.5. 실행

![image-20240805232310187](/images/2024-08-05-review-spring-3/image-20240805232310187.png)

![image-20240805232322192](/images/2024-08-05-review-spring-3/image-20240805232322192.png)

