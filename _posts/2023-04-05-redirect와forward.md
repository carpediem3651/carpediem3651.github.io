---
layout: single
title:  "redirect와 forward"
categories: SpringMVC
tags: [Spring,SpringMVC,redirect,forward]
toc: true
author_profile: false 
sidebar: 
    nav: "docs"
--- 

# 1.Redirect
<img src= "https://dsm04pap002files.storage.live.com/y4mD2NXTSI1OxhHUNw7H98eq4UxThCJ_wmdIs0M7_lv4wZ8giJSxrb_IbjtWK1Gzj99doSJvKEq7ck7fy2I3zkVTnpdXF5RvPEVFUcTd9390KUCThdN-Cr2oKg7qt61CkBo7G7FueT0-FBO2qvnlP5FGU0kEBKtHbJtKayP9Sitxv9o9vkwkQdU3iGx4T9rRJht?width=1184&height=557&cropmode=none">

redirect는 브라우저에서 받은 요청을 다른 URL로 재요청한다. 브라우저에서 1.요청을 하면(수동, GET/POST둘다 가능) 헤더에서는 302 즉 다른 URL로 재요청하는 300 Redriect가 입력되고 다른 URL로 요청되는 위치를 Location에 쓰여진다. 2.응답을 받은 브라우저는 새로운 위치(login.jsp)로 3.요청 재요청(자동, GET만 가능)하게 된다. 요청후에 작업이 완료된 login.jsp에서 브라우저로 응답한다. redirect는 요청이 두 번 발생한다. request가 두 번 발생하는 데 두 request는 다르다. 

 

일상생활에 비유하자면 서비스 센터에서 담당이 달라 다른 번호를 알려주고 재연결을 요청하는 것과 유사하다. 예를들어 컴퓨터 AS를 맡기기위해 서비스 센터에 전화를 했다. AS를 요청했고 서비스 센터에서는 자기들의 담당이 아니기 때문에 AS센터로 다시 요청하라며 번호를 넘겨준다. 그러면 넘겨받은 번호를 통해 AS센터로 다시 연결하고 AS가 진행된다.

# 2.Forward
<img src= "https://dsm04pap002files.storage.live.com/y4mdggzpbNkQuemtqkr_WOUvNblV_y9rXeuqr_PZKWRVsy9s-_bA-lRrEHTTmDuOgYyRHIG4nO_chkRNelE_cxq7zA4VZsJQijSqLaRS96utIxT7VMjR9QI2Aq8nOeqO2_SPGUuiv4oDjKKb1_Q3EQFASiTcQcwNUxzhUhkXxVu-DjAQfXH8fhnBrXY1RGlrAr7?width=775&height=411&cropmode=none">

orward는 redirect와 달리 요청이 한번만 발생한다. 브라우저로부터 요청을 받으면 잘못된 위치로 요청받았기 때문에 요청받은 write.jsp는 다른 위치로 연결(forward)을 해준다. forward는 카드사 대표전화에 분실신고로 전화하면 대표전화는 담당이 아니기 때문에 분실신고 센터로 자동 연결해주는 것과 같은 이치다.  

# 3.Redirect와 Forward 비교
<img src= "https://dsm04pap002files.storage.live.com/y4mkqVheunu8rpb0Gw-ASV33AFPHDVExcBt1DPXo9dguiTBsjkkKa9GFR2SWgABRJ1LGoIWFw5Fu_GR7XKuv4qZ8jPD1MQL7SnW47BYCTDgwWaqGfmCyBHG6Panmn19-1oKjZMdJ8909W-uxWdicLKfu-z3-ZtIzQqflrfOCcI5WOieQ0tY_vuf_e0KApKhg5B9?width=1193&height=464&cropmode=none">

<img src= "https://dsm04pap002files.storage.live.com/y4mZzY_7c7zCI_zfu5wRF2x-Nk36pZV8rJgZ60VIOLLXYdr4QuwOymviXrAp4XCsFSF7vZ1_ShLm0WBFgwD1e6C7a1f2bG2eCeAe4WxsPBNtxCNk_lBh_7i1D3-WivaL18RsyqLbyof2OYnjjrBjWgl__PE3w9KKQAAmiFfZ2uKO_G2yM51nCVUum8S-sRotn_P?width=1080&height=147&cropmode=none">

---
출처  
스프링의 정석: 남궁성과 끝까지 간다(패스트캠퍼스 강좌)