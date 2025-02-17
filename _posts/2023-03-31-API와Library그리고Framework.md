---
layout: single
title:  "API,Library,Framework"
categories: CS
tags: [API,CS,Framework]
toc: true  
author_profile: false 
sidebar: 
    nav: "docs"
--- 
# 1.API(Application Programming Interface)
## 1.2 정의
응용 프로그램에서 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스. 이미 만들어진 기능을 사용하기 위한 파이프라인, 다리

ex.맛집 공유 프로그램을 만드는데 지도를 나타내는 프로그램이 필요하다. 하지만 직접 지도 프로그램을 만드는 방식은 오랜 시간이 걸리기 떄문에 지도 프로그램을 만들어 제공하고있는 G사의 서비스를 이용한다. 서비스를 이용하기 위해 중간다리인 API(/map/위도&경도)를 이용해 활용한다.

<img src= "https://dsm04pap002files.storage.live.com/y4mQrjHkvMbRnf2K9jt8_1vWdast-Wc3SRyxsnIwCDjSBl4J9wwBFcho5KulPOZFJpHPtwe30cEZXHGqX15Ffua5U_9J5ian8wkbz3bP11deGCXks_qbKfyb59hkKZAwXe-6eqjgt6IRoXN6-v9f4zrWDBa7mUUn_gM9GX4QoDHYtPO7vZjQ97TOQ2R1Td2BdqG?width=661&height=336&cropmode=none">

## 1.2 특징
- 구현과 독립적으로 사양만 정의되어 있다.  
- API에 따라 접근 권한이 필요할 수 있다.  
- Java API, 여러 기업들의 오픈 API

# 2. Library
## 2.1 정의
응용 프로그램 개발을 위해 필요한 기능(함수)을 모아 놓은 소프트웨어. 

ex.학생들의 시험점수 평균을 내는 프로그램을 만들고자한다. 그런데 X라이브러리는 평균을 구해주는 기능을 가지고 있다. 그래서 굳이 평균을 구하는 기능은 구하지 않고 단지 X라이브러리에서 끌어다가 쓰면 개발을 보다 쉽게 할 수 있다.

<img src= "https://dsm04pap002files.storage.live.com/y4mtYdoBYjwCHT_gx-j8HqOvuIByDrLopNqRJcQZfmqBn56ed4F-FNjYlbJjL2Z9vVWzROY7QzZ97JpSurzABQWGcOuaDukLLcOQajjhSDeKAVcz4AGDkfsugDhJfila3v0jA6F3gRtceKdDJbWm-LHw6O3JfleO7SRYbAm2cSOwELhoYobSDqVvs3nJ6BTXdVk?width=692&height=387&cropmode=none">

## 2.1 특징

- 독립성을 가진다. (해당 라이브러리는 다른 라이브러리에 의존하지 않는다.)  
- 응용 프로그램이 능동적으로 라이브러리를 사용한다.  
- Apache Commons, Guava, Lombok, jQuery  

# 3. Framework
## 3.1 정의
Frame(틀,뼈대)work(일하다). 정해진 틀 안에서 일하다. 응용 프로그램이나 소프트웨어의 솔루션 개발을 수월하게 하기 위해 제공된 소프트웨어 환경

ex.자바를 이용해 서버프로그램을 만든다고 가정해보자. 서버 프로그램을 만들기 위해 Socket, OutStream, Request를 생성하고 컨트롤러와 로직을 '직접' 작성해야한다. 많은 노력과 수고를 필요로 한다. 하지만 이런 작업을 Spring Framework를 이용한다면, Spring Framework가 제공하는 기능을 사용하면 앞서 했던 수고로운 일들을 쉽게 할 수 있다.

## 3.2 특징
- 상호협력하는 클래스와 인터페이스의 집합
- 응용 프로그램이 수동적으로 프레임워크에 의해 사용됨
- Spring Framework, Junit, Ruby on Rails

---
출처  
[[10분 테크톡]🙆‍♀️티버의 API vs Library vs Framework](https://www.youtube.com/watch?v=We8JKbNQeLo&ab_channel=%EC%9A%B0%EC%95%84%ED%95%9C%ED%85%8C%ED%81%AC)
