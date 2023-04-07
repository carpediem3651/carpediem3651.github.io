---
layout: single
title:  "print,println,printf 구분"
categories: Java
tags: [print,println,printf]
toc: true
author_profile: false 
sidebar: 
    nav: "docs"
--- 

# 1.system.out.print(출력대상)
- 상수, 기본자료형,String형 변수가 출력대상으로 올 수 있다.
- 서식지정자(format specifier)에 영향받지 않는다.
- 엔터 입력시 버퍼에 개행문자는 포함이 안된다. 즉 엔터를 눌러도 줄바꿈 되지 않는다.

```java
public class Main {
    public static void main(String[] args) {
        System.out.print(123);
        byte b = 10;
        System.out.print(b);
        long l = 100L;
        System.out.print(l);
        boolean bl = true;
        System.out.print(bl);
        char c = 65;
        System.out.print(c);
        String s = "한울별하";
        System.out.print(s);
    }
}
```
실행결과  
12310100trueA한울별하

# 2.system.out.println(출력대상)
- 상수, 기본자료형,String형 변수가 출력대상으로 올 수 있다.
- 서식지정자(format specifier)에 영향받지 않는다.
- 엔터 입력시 버퍼에 개행문자가 포함된다. 즉 엔터를 누르면 줄바꿈 된다.

```java
public class Main {
    public static void main(String[] args) {
        char c1 = 'A';
        System.out.println(c1);
        int i = 1;
        System.out.println(i);
        System.out.println((char)(c1+i));
    }
}
```

실행결과  
A  
1  
B

# 3.system.out.printf(String 서식, 값들)
- 서식 지정자에 영향 받는다.
- 엔터 입력시 버퍼에 개행문자가 포함 안된다. 즉 엔터를 눌러도 줄바꿈 되지 않는다.

```java
public class Printf {
    public static void main(String[] args) {
        double d = 3.14;
        int i = 2;
        System.out.printf("%f X %d = %.2f",d,i,(d*i));
    }
}
```
실행결과  
3.140000 X 2 = 6.28

# 4. 서식지정자 모음
<img src= "https://dsm04pap002files.storage.live.com/y4mZOFn453jpB3b8Qa4ExskSnkimGcgGMiIoUeqwKiwech5liEC9nYpJ8Fe5VZvUgURgdZmTTPDOLzvIHBAVivyThlvc2nSGqicC3gIj1KYGm-lfW1D3NJC4dEBK7f0RRe908gVoU5Lyor09AMziKWra9PCL6dx-HuiNZO6JyD0z-m_YgEWGnFi32yZ-1jZG_kx?width=396&height=581&cropmode=none">

--- 출처

[별무리의 기록실]("https://starrecode.tistory.com/10")