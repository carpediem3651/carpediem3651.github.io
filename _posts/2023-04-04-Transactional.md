---
layout: single
title:  "@Transactional"
categories: SpringDI와 AOP
tags: [Spring, Transactional, AOP]
toc: true
author_profile: false
---
<img src= "https://dsm04pap002files.storage.live.com/y4mi-yG9sv4ejf90VrMmM0AlZwQ2175acolPg3VMnjVhL0zNNA1XU-2gP5QNuflcpy8TJGMbH0vTXAf9jwnXFdeOuLKgMe-QwPXlZVcGWKj53jouRROvzIT0rdig_hAepxVQbGtE46GNubBeUTJGHZzEONXQoaIER4pbx3Cx4lv8gtRtzCm_gilLtMx8Hsx4UeU?width=512&height=268&cropmode=none">

# 1.TransactionManager
<img src= "https://dsm04pap002files.storage.live.com/y4m28EwmPmtZmwKnnoW1aIQDJUKQ8Iz4EjaC6hdBhWyHnW5h66UNNsjLUGurMy5io7A-RXT_c8QtH4SR8S3t7J3ZKeJBUd2VKmvRQmPgID0xbLEBap7OHudZNDADVCl7bGm6OVkhAdA12lD2cUZ9WfyOGiOYdk7D7ykmTRZtaksBnxTSEKqcD-kav-By6ruasGc?width=617&height=412&cropmode=none">

<img src= "https://dsm04pap002files.storage.live.com/y4muh_mrO-VaFVhH_5N6_i6LjDQZLgUZ2ORixcgHVyf_YHsoIUruRvWBOSfM_-t5j0eatXR36F07PourL8b3z3p1D4YunKBHk4tGTECKefC2vHkJ8TI57WqzAI2kABznjgeUuQO67QHagJIgOp_GMj0EDwQHb2e70rTPj0pmcS5m1gLVmI6hfvETseJbyGrT31X?width=836&height=396&cropmode=none">

하나의 메서드는 하나의 Connection을 가진다. 하지만 하나의 메서드에 하나의 Connection을 가지면 중복된 메서드의 Connection은 개별 커넥션을 갖기 때문에 Tx가 안된다는 문제가 발생한다. 예를들어 UserDao의 deleteUser(100);를 실행하면 메서드에 해당하는 Connection이 commit되면서 100이라는 키를 가진 유저의 정보가 삭제될거다. 그런데 여기에 deleteUser(200);을 실행한 후 rollback을 해야하는 상황이 발생하면, 이미 deleteUser(100);이 실행된 Connection은 commit 되었기에 rollback이 되지 않는다. 이 문제를 해결하기 위해선 두 메서드의 Connection을 하나의 Connection으로 관리될 필요가 있는데, TransactionManager가 그 역할을 한다. 

<img src= "https://dsm04pap002files.storage.live.com/y4mi4wiRE9BH0LwPe7JhsFYq_JgsgFmB3pnKX8nxQ5t4FYBYgGQvfeCTy7Qh94T4wJ0YpqTTZHJfl2zrw3OBgOxcgNKaXEgeu89SbRuJxdQizGsZVJ0y1fPkI9qJ1qqqmSEzt6HgV7Qw3YVPlyhBDQv-LabZuLW4h9vl0Cs4BTWaF_oPk5srYn4bcNFVmxLUGj8?width=1091&height=362&cropmode=none">

## 1.2 TransactionManager로 Transaction 적용하기
Dao에서 Connection을 얻거나 반환 할 때 DataSourceUtils를 사용한다.

- TxM 설정코드
<img src= "https://dsm04pap002files.storage.live.com/y4meixuheF46pavA4Uq1adHjeIOSurNCQ5WJ8ioWheO7CF8O7Y13QIdKa5mFDure3ROwlpvjxQ6AU-XtxiqiocbrZzR-RMWs6gx_zn0C-HQSQxSSrFjzf7STKJ-XJO22SLlNxg6hmzOAxdftsVVC6smHASpOSNAWhQj_vRgDISdzX-hGsmUwD-_UB4uAL7oy9fY?width=746&height=468&cropmode=none">

- TxM 적용
<img src= "https://dsm04pap002files.storage.live.com/y4mGkKoAU3OqQifEjgjefk8hkxXkuLwAjIK5VAjym2q4vbeBfvuXy6DZvFOxb8aapyEl2LdYDGDC4whxqHzk5xGwJSLJDcXF36_579JEiMZXEB-bEAA1SC5-UiqVxVWR5Mk28OON22JN2D4hrT1tBxJXXRuaTcP4Py-KZPAXzaQxtOgb9JQFn8m9grqieXb0R3Y?width=1081&height=474&cropmode=none">

TxM로 Tx를 적용하면

①new DataSourceTranscationManager(ds);를 통해 TxM를 생성한다. 그리고

②tm.getTranaction(...);를 통해 Tx의 속성을 정의하고 Tx는 시작된다.

③try ~ catch문을 통해 Tx가 실행되는데 코드를보면 a1Dao.insert();가 모두 성공했을 때 commit이 되고 실패 했을 시 rollback한다. a1Dao.insert(1,100); 과 a1Dao.insert(1,200);은 서로 다른 Connection을 갖는다 그래서 Tx이 따로 실행되지만 TxM을 통해 이 Connection을 하나의 Connection으로 묶어 동시에 Tx가 가능하게 된다.

- Bean으로 TxM 설정


<img src= "https://dsm04pap002files.storage.live.com/y4mQNFLBopmWzQ62xHv7tj5SxNmcbnWt-6PW79R-QR2sVGOD9sFZWNChl_OLoea4VHe1ge-ZiwzulJpsK4PzvSMm3CDegUth5beCpZ2ov9FlGw2v528wd7u51y9cpNNqEUEcZYAgKsH-ZiWwVAGbpLy-_yqmdQzdBxi-ptk_Jc933j_8FhFpqJ3FN9fyk34H1L6?width=1114&height=122&cropmode=none">

TxM을 사용하기 위해 앞에서와 같이 코드를 작성하는 방법도 있지만 간편하게 위의 사진과 같이 Bean으로 등록하는 방법도 있다. 개인적으로 Dao에 TxM을 설정하기보단 xml의 Bean으로 설정하는게 더 낫다고 생각한다.참고로 tx:annotation-driven/은 앞으로 살펴 볼 @Transcational을 사용하기 위해 설정한다.

# 2.Transational
<img src= "https://dsm04pap002files.storage.live.com/y4moMFhshJVeeqHkFAQnXx3SfT8lb6mfBY0-YPIpbAIEQOR-TgaLFYDhX-WTNgUb-eZmt79O5dI8G_QWkq_w1Ta72qtNt2sh4N-b6Ykb9v60cnNesAgTTn1yMTX4o7EPtRrCsi9tMnE6KF-PzIWPvvlMRUkqVUb4rOuAfZrw-PrEvurJLcnNCeXsqRb4k2YP5ay?width=1115&height=441&cropmode=none">

 @Transactional은 AOP의 주요 개념인 핵심기능과 부가기능을 분리하는 방식을 사용한다. 위의 코드를 보면 빨간색 박스를 친 코드가 핵심기능을 담당한다. 이외의 코드들은 모두 부가기능을 담당한다. 부가기능은 항상 반복되기 때문에 분리할 필요가 있는데, @Transactional은 이 두 코드(부가기능, 핵심기능)를 분리한다. 핵심기능 코드를 @Transcational이 붙은 메서드에 넣어 사용하면, 스프링은 부가기능을 따로 설정하여 개발자 입장에서 핵심기능에 더 집중 할 수 있게 한다. @Transactional은 클래스나 인터페이스도 붙을 수 있다.

<img src= "https://dsm04pap002files.storage.live.com/y4min33j6BrxEf2hMnc9CSp2_KMmaDI46LWpL6nkM8cNU9Y553xMXaOHlOYGjggjZE92JpXSYvgkjJFfw3du27lYe5MgAojEkRpleMmT0E5eCOFCyRQHRHjJlYrirkgtd7ssIfQM6MqnJZAQ3tg60F-QjutpfCUekLy3LRw5bOOqwNDoXPOLLuPIpVeb97SbPC_?width=1217&height=350&cropmode=none">

## 2.1 @Transactional의 속성
<img src= "https://dsm04pap002files.storage.live.com/y4m2VvEcKeGghVprclbwEnRMsdYl_40sLoVlWl_q3iDobgT9bRrULWbMAIh3YjxoiiL1DpVLgKmkpXdHi_ZKMJbwrYV-qxpaJwh9oEsW3ReD1mV3-2zwQOfLDBONavedSPF-RHk0yIDO9c876QGzTnBLMrnKniVwLyRTJPVBv5MZvzjRG52VR7dkvvguLgILxgA?width=1080&height=397&cropmode=none">

## 2.2 propagation의 속성 값
<img src= "https://dsm04pap002files.storage.live.com/y4md0bMclmTWT6RpHoYYfXFw41NM3DigHHDixMk3RGJpVcXX0CKBaniX3dOcqjDGc-wh4XTbV8GF7_OcO_hwdmH0EPY8vS_L2Tqh-rcLD3FgKDL-hMOpaPfHN618OMYMf-X9eXhzJDU1p309uUPf2_QNgkYSq6gHx-NThshkmTKvVGGjzWSx9lcBMn98P2Ubshz?width=1069&height=385&cropmode=none">

- REQUIRED
<img src= "https://dsm04pap002files.storage.live.com/y4mkdKozB1DDnn02wDE7Qhal2VIFt13ixx_JN2clR58MYNx2blD7xTP_0o1y9r8vBXH2zofwLwxQE8e-uVuaO0GGhIRHFybqbzu1WGZSfQzxBbYt9aEEEASYLIX0IoxC8WiPFa2fs6nX3AWZ_BlW2aGYD_XMlPQ1RPXAJokMJcPtcOhZoiiOsvYcfOrUu0Ufde4?width=1036&height=609&cropmode=none">

- REQUIRES_NEW
<img src= "https://dsm04pap002files.storage.live.com/y4micTVJDnEQVrIqHzpDJLoj1AnzSXmEyYB-8IGMrceJTiOOve6R1IjKz6Q0PGUE7GMEKrJLYbMMngWQa9BV2sNVPTqrkt6VfztM18WFTELivktkqeU2ZJKKAkD4p2c-SxKYVitbMxBqUUW_vyR9jQkEUeMh5vocIXXf9_y6YNtokm4-bRbyN93u-6tqurIfXtL?width=980&height=611&cropmode=none">

