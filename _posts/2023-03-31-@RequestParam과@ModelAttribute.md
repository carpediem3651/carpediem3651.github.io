---
layout: single
title:  "@RequestParam과 @ModelAttribute"
categories: SpringMVC
tags: [Spring,SpringMVC]
toc: true  
author_profile: false 
sidebar: 
    nav: "docs"
--- 

<img src= "https://dsm04pap002files.storage.live.com/y4mi-yG9sv4ejf90VrMmM0AlZwQ2175acolPg3VMnjVhL0zNNA1XU-2gP5QNuflcpy8TJGMbH0vTXAf9jwnXFdeOuLKgMe-QwPXlZVcGWKj53jouRROvzIT0rdig_hAepxVQbGtE46GNubBeUTJGHZzEONXQoaIER4pbx3Cx4lv8gtRtzCm_gilLtMx8Hsx4UeU?width=512&height=268&cropmode=none">

# 1.@RequestParam
 @RequestParam은 요청 URL의 파라미터를 연결할 메서드의 매개변수에 붙이는 애너테이션이다. 

 ## 1.1 @RequestParam을 생력하는 경우
 <img src= "https://dsm04pap002files.storage.live.com/y4mD47kU2ezjHq_zdL6aHpe9JtlR9pryCwW0qSCzqCuMrGU9jO96ylVyGvzPGV0ZG2v_bf4ET1wogHL54tu_2YL7pCcB5swnvJX2vwHppmY5nZl7zzZGRwd_z5gs5V4K3LOkrXWULYq57gJZbv-t2uuSzmWR0bq27PXJRNfKZwB7riX1wtrgSJK7UMcSugvvfFr?width=1206&height=465&cropmode=none">

  @RequestParam은 매개변수로 파라미터 이름을 나타내는 name과 @RequestParam의 필수 여부를 따지는 required를 매개변수로 갖는다. 위의 그림과 같이 required가 false일 경우 @RequestParam을 생략 가능하다. 하지만 required값이 필수가 아닐 경우 null과 " "(공백)이 요청값으로 들어오면 타입에러가 발생한다. 이런 오류를 막기위해 defaultValue를 1로 설정한다.

<img src= "https://dsm04pap002files.storage.live.com/y4mYoMxDeJzfesjHQiTnroHNHOkMcQXETH5EmCHwlfQ73b8s-w80Of4Rxv4amTjTmyUBTPcrIMpsvxWuTQsSpQOe5cbpA08cCmZzc4Bv1JbUGoheGsvfZHIY_cAe3TqN8iO6BUsXAwTjNmT_U_J1EOKed3eR8GAMn_6LZ099O4ffF9jo85th1Av_ZJnYkPNlaMP?width=1199&height=159&cropmode=none">

## 1.2 @RequestParam을 생략하지 못하는 경우
<img src= "https://dsm04pap002files.storage.live.com/y4my0CGAcOX3qvCqzpChBW4dPmoUmEFJS0DYkpt5R7PWzHhhW2_ecSYxBZQ0i_H47KnhzE5jKrkMl0RWPE4fWYUqI-U-5qQXRdZuMtrDs3RlCg7XeZPQ1ie4Pw77oqh3ii-TTE6HIKSXXk1eHqTiMVhUJlh41bduBgXCm378HT2HZm0_gBLEFjzPcKUTRROmNoe?width=1226&height=372&cropmode=none">

@RequestParam의 매개변수 required의 값이 true면 @RequestParam은 생략이 불가능하다. HTTP요청을 통해 확인해보면 그림에서 보이는 바와 같이 year값이 null일 경우 요청값이 잘못됐기 때문에 400 Bad Request 즉, 클라이언트 오류가 발생한다. 

# 2.@ModelAttribute
@ModelAttirbute는 애너테이션이 적용된 대상을 Model의 속성으로 자동 추가해주는 애너테이션이다. @ModelAttribute는 반환 타입 또는 컨트롤러 메서드의 매개변수에 적용가능하다.

## 2.1 매개변수에 적용
<img src= "https://dsm04pap002files.storage.live.com/y4mOWFZ1_lAEVRsMWIeG4aRIukThcfUj82z9xoXSACGaUkkK1cu4563IsCgCEgACYPY2I69R4q8v9-aKGEPgGOVmuXwuWJF9JgQH7ugHG_hhcBRw02vK1OiTwL9t8tACWYAMzf4CBMpyf_iOwKCobyBNCkY4c_pQ9TNsDDZ9aXjiEgT5GvhlO9diLb7TsrhihDM?width=1084&height=431&cropmode=none">
<img src= "https://dsm04pap002files.storage.live.com/y4m1TP5Ej3vVnY4N-xqV_wFoVv0PITY7BCUUKBbBWw6IevOpqIGaZiknaNbXQvlU69jnkbVGk7KY_ijtMdcWcHT8ucI2d155rtu3hHgHG7Omp825Xke7N3ok5YDREOX_t6BoLlQ-Zl_5-1RjxYPOV6ljcgsI4S6JFsRGpwPInt9h_dU6nbWSXBM3fASkl-vbpMf?width=1071&height=411&cropmode=none">

매개변수에 @ModelAttribute를 사용하면 Model 속성으로 매개변수의 키와 값이 저장된다. 그림에서는 키의 값이 'MyDate'로 맨 앞글자를 소문자로 쓴 'myDate'가 Model의 속성으로 저장된다. 이와 함께 'MyDate'의 value인 'date주소'가 Model의 속성으로 함께 저장된다. Model의 속성 값이 저장되면서 더 이상 'MyDate'키를 추가하는 코드(m.addAttribute)를 쓰지 않아도 된다.  

## 2.2 반환타입에 적용
@ModelAttribute가 반환타입에 적용되면 메서드의 호출결과를 Model에 저장한다. 여기에 더해 값을 직접 호출한다. 호출까지 함께하기 때문에 호출하는 코드가 삭제된다.
<img src= "https://dsm04pap002files.storage.live.com/y4mzLAzzKBmuGZhLDuLFv0Hbt8Kj4ZbFmsPrNAnFfRnOsz9yD_qaU64yKI6rLtUppHS8MmkB5QVlATYSc96B94f6lz84Qrxy7nZinD_YaXcgC0wacZXCa7G9LedTFXtAK8pIXmuDJXrvysftM0lzK3_xFmil6JGcsKP_KWo8RfkIfK95VmW9kaY4QAeL7qLU8e5?width=988&height=144&cropmode=none">
<img src= "https://dsm04pap002files.storage.live.com/y4mXgaqaQar4S_RQo1_Fl56cAo0beKnI6E7FedsQngY6xf8i-UAH11mSKn-2Q0qgNT0RAxPYH9z7-5u0POPKlRud9vGsLdfC87Gsyf5mLd3tLzd4deCAr0ryYJwL6M_OKvAKLy52XL4-wAnvl2hRnGZ0qrluAzfb0_DLjNpLBvmA1UjAa9yRANlh5en6Kawz8nl?width=906&height=459&cropmode=none">

---
출처:스프링의 정석 : 남궁성과 끝까지 간다(패스트 캠퍼스 강좌)