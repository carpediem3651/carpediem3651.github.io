---
layout: single
title:  "Connection Pool"
categories: DB
tags: [DB, Connection Pool]
toc: true
author_profile: false
---

WAS(Web Application Server)와 데이터베이스 사이의 연결하는데에는 많은 비용이든다. Connection Pool은 이를 해결하기 위한 기법인데 하나 둘 씩 알아보자.

# 1.커넥션 풀(Conncetion Pool)이란?
<img src= "https://dsm04pap002files.storage.live.com/y4mWXaUWOWcQCIeYfvsdbiWNPaw7CNsMseoD6XlAYxffrSlusf0X8eWCZ_IiAiCFW_Bd3Ua-INDgo2jmcSyAiSdXvDPHBJ0jI_AHimhdr7KLEodaHM-4o4o4lXPOn_Dsw1DSKCkEYPPdbz79xOToq6ULUQ82BnFe9O48BLFN0b9XG5kfM6_7Nj_CDwnXHdz4AUU?width=580&height=276&cropmode=none">

- 출처:https://www.ibm.com/developerworks/data/library/techarticle/dm-1105fivemethods/index.html 

커넥션 풀은 WAS와 데이터 베이스가 연결된 Connection을 미리 만들고 이를 Pool로 관리하는 것이다. 한마디로 Connection이 필요할 때 커넥션 풀의 커넥션을 이용하고 반환하는 기법이다. 어떻게 보면 '비디오 대여점'이라고 볼 수 있다. 미리 만들어 놓은 커넥션을 Pool에 관리하면 연결비용을 줄일 수 있고 빠르게 DB에 접근할 수 있다. 또한 커넥션 수를 제한할 수 있어서 과도한 접속으로 인한 서버 자원 고갈을 방지할 수 있으며 DB 접속 모듈을 공통화해 DB 서버의 환경이 바뀔 경우 유지보수를 쉽게 할 수 있다.

- 커넥션 풀의 장점
  
  1.연결비용을 줄일 수 있다.  
  2.빠르게 DB에 접근할 수 있다.  
  3.서버 자원 고갈을 방지할 수 있다.  
  4.유지보수를 쉽게 할 수 있다.

# 2.HikariCP
HikariCP는 JDBC의 커넥션 풀 프레임워크로 대중적으로 가장 많이 사용한다. 다음 아래의 그림을 통해 HikariCP에 의해 커넥션 풀이 어떻게 작동하는지 동작원리를 살펴보자.

<img src= "https://dsm04pap002files.storage.live.com/y4mqlh0aEq-GqBAI7WfjNNkCL1-HZ-or_5HYHgBzeNJMvmjxMlk58V6sxLGbjrnUL-jbeRW3FyYE4j3LBdYVnnFnXxyDfF38qD8HsjBslvpp7ZSZ20tyrkn9kZ3T4hBw3GnXfA20JTsttziNba-uK_o486XIp-dbg9B8ix3cCxZ87M7lw0FcanXJbOmeJ9FJqEx?width=873&height=326&cropmode=none">

- 출처:https://code-lab1.tistory.com/209

그림과 같이 Thread가 커넥션을 요쳥했을 때 사용할 수 있는 커넥션이 존재하면, 해당 커넥션을 반환한다.

<img src= "https://dsm04pap002files.storage.live.com/y4muqNScYGRx-gSw2M5XONGm6xh2UG9wDpE8WL2KGT0b_wXqgOcmETAHxHKuTAyG7UR4JjBUcIvNcY_q1CfwvsbATE3aNz9W-LunkQR5aWwW3Jt2uaBh9RQQkCn8qh33pE8b11FUKSziJiGaXxPRpXCAJY4qmKNqzZE2yO8Oa0SAf9yWkqLMigBRnJ9Hatdn3do?width=707&height=391&cropmode=none">

- 출처:https://code-lab1.tistory.com/209

만약 사용할 수 있는 커넥션이 없다면, HandOffQueue를 Polling 하면서 다른 Thread가 커넥션을 반환하기를 기다린다. 다른 Thread가 커넥션 풀에 커넥션을 반환하면, 커넥션 풀은 HandOffQueue에 반납된 커넥션을 삽입하고 HandOffQueue를 Polling하던 Thread는 커넥션을 획득한다.

---
출처   
[코드 연구소](https://code-lab1.tistory.com/209)
