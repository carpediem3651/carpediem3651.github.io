---
layout: single
title:  "EL(Expression Language)"
categories: JSP
tags: [JSP]
toc: true
author_profile: false 
sidebar: 
    nav: "docs"
--- 

# 1.EL(Expression Language)
:
EL(Expression Language)은 콤마(.)와 대괄호([])를 사용하여 자바 빈의 프로퍼티나 맵, 리스트, 배열의 값을 보다 쉽게 꺼내주는 기술이다. JSP에서는 주로 보관소에 들어있는 값을 꺼낼 때 사용한다. JSP에서 쓰던 <%=값%>을 안쓰고 ${값}을 사용해 간단히 표현하기위해 쓴다.

<img src= "https://dsm04pap002files.storage.live.com/y4m5gQH4jQcvSW8oq0EUjKVF8SEEPAVsP0Nfx401LB7WK2I3co0HsqtmynaMTqWRLb9Mi3bGJr3e9wYfPLZkJ6fiRzsCY3M0w63ayoTxsD67-Pc_M4lghkuzod-uHwdnsVGk4jZ-XX95PNooi9pe2h-KcvS1AlU0N-I0xhLSO1qxInrFJk0EFaSHNZuHcrYFhLs?width=618&height=552&cropmode=none">

## 1.2 EL표기법
:EL은 ${}와 #{}를 사용하여 값을 표현한다. ${}을 '즉시 적용(immediate evaluation)'이라 부르고 #{}을 '지연 적용(deferred evaluation)'이라 부른다.  ${}은 객체 프로퍼티 값을 '꺼낼 때', #{}은 객체 프로퍼티 값을 '담을 때' 사용한다.


<img src= "https://dsm04pap002files.storage.live.com/y4m96DKcjxagJExt--VVz47hZx9l5QGFazvEdh1BogDnni4Xgufc18Xu2L3230Ba6FuVGZP3A0Cgy8HM8dXZgXmZsTezBgSfRaVL9cy5Ez0e_4kdy-5hcdsX1M12XeiYg6GEE858WwT0igU_gGZ12pnJL43NgiPGIEZyCDocV-QpHThprfQI468auEhnYoxwux5?width=396&height=285&cropmode=none">


## 1.3 리터럴 표현식

EL 블록에서 사용할 수 있는 값은 문자열, 정수, 부동소수점, 참거짓(Boolean), 널(Null)이 가능하다.

EL표현식
- 문자열: ${"test"}  
- 문자열: ${'test'}  
- 정수: ${20}  
- 부동소수점: ${3.14}  
- 참거짓: ${true}  
- null: ${null}  

실행 결과값
- 문자열: test  
- 문자열: test  
- 정수: 20  
- 부동소수점: 3.14  
- 참거짓: true  
- null :  

## 1.4 값 표현식
### 1.4.1 배열에서 값 꺼내기
EL 표현식
``` java

<% // 값 준비

pageContext.setAttribute("scores", new int[] {90, 80, 70, 100});

%>

<%-- 배열에서 인덱스 2의 값 꺼내기 --%>

${scores[2]

```

실행결과
```java
70
```

### 1.4.2 List 객체에서 값 꺼내기
EL 표현식
```java
<% //값준비
List<String> nameList = new LinkedList<String>();
nameList.add("홍길동");
nameList.add("임꺽정");
nameList.add("일지매");

pageContext.setAttribute("nameList", nameList);
%>

<%-- 리스트 객체에서 인덱스 1 값 꺼내기--%>
${nameList[1]}
```

실행결과
```java
임꺽정
```

### 1.4.3 Map 객체에서 값 꺼내기
EL 표현식
```java
<% // 값 준비

Map<String, String> map = new HashMap<String,String>();

map.put("s01", "홍길동")
map.put("s02", "임꺽정")
map.put("s03", "일지매")

pageContext.setAttribute("map", map);

%>

<%-- 맵 객체에서 키 s02로 저장된 값 꺼내기 --%>

${map.s02}
```

실행결과
```java
임꺽정
```

### 1.4.4 자바 객체에서 프로퍼티 값 꺼내기
EL 표현식
```java
<% // 값 준비

pageContext.setAttribute("member", new Member().setNo(100).setName("홍길동").setEmail("hong@test.com"));

%>

<%-- 자바빈에서 프로퍼티 email의 값 꺼내기 --%>

${member.email}
```

실행결과
```java
hong@test.com
```

## 1.5 JSP에서 제공하는 EL 기본객체
<img src= "https://dsm04pap002files.storage.live.com/y4mcqvfVeo5QrgVNL1Fo2Apqacdy2Z8yBrGV-wtSN_KtBdfiWrSZ6aCZ28UyKydl9IHwhhYft-b3mnRyTXxlqFhy44Z4rtFC-7F5yqvRk_47fEOmvR81Mk_Tp7ZEmJyzaxOGEvpOTIPm1ZOEg5S4AmbF8XhDXHrwvINxVP9sV7Xifgcx5kFwPwSDzdwimsIRHVP?width=1082&height=513&cropmode=none">
<img src= "https://dsm04pap002files.storage.live.com/y4mdnX91DkedLekm0jhDNBFeefU1l9rDIr4Xm_jdHPAG6Ez1RUK6QWVlYNY9n4YnNKP20JkRL7NO7dZWoIhHy4M69QqsG1TADViYNA0W_rmn3izxBYz19TYJopKng_v7qdX09PLYPCVvNaSILHXwZNCMTiNslU5XX0JdU8dn2gMYf0ZXL19jQtPwWX7fgCwpzxo?width=1085&height=365&cropmode=none">

---
출처  
- MVC아케틱처, 마이바티스, 스프링으로 만드는 실무형 개발자 로드맵 자바 웹 개발 워크북(저자: 엄진영, 출판사:프리렉)  
- 스프링의 정석 : 남궁성과 끝까지 간다(패스트캠퍼스)


