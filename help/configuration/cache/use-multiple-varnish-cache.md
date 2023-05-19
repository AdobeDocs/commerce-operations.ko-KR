---
title: 여러 Varnish 인스턴스를 사용하여 캐시 지우기
description: 여러 Varnish 인스턴스에서 캐시 지우기가 작동하는 방식을 알아봅니다.
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 여러 Varnish 인스턴스를 지우는 캐시

Adobe Commerce 및 Magento Open Source은 즉시 여러 Varnish 인스턴스를 지원합니다.

이 항목에서는 Commerce를 사용하여 여러 Vanish 인스턴스를 구성하는 기본 사항을 보여 줍니다.

## 여러 Varnish 인스턴스를 제거하는 구성

Commerce는 다음을 사용하여 Varnish 호스트를 구성한 후 Varnish 호스트를 제거합니다. [`magento setup:config:set`](../../installation/tutorials/deployment.md) 명령입니다.

다음을 사용해야 합니다. `--http-cache-hosts` 매개 변수를 사용하여 쉼표로 구분된 Varnish 호스트 및 수신 포트 목록을 지정합니다. ( 공백 문자로 호스트를 구분하지 마십시오.)

매개 변수 형식은 다음과 같아야 합니다. `<hostname or ip>:<listen port>`, 여기서 을 생략할 수 있습니다. `<listen port>` 80번 포트면

예를 들어,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

그런 다음 상거래 캐시를 새로 고칠 때 모든 Vannish 호스트를 제거할 수 있습니다(이라고도 함). _청소_ 캐시)를 관리자 또는 명령줄에서 사용할 수 있습니다.

관리자를 사용하여 캐시를 새로 고치려면 **시스템** > 도구 > **캐시 관리**&#x200B;을 클릭한 다음 을 클릭합니다 **Magento 캐시 초기화** 을 클릭합니다. 개별 캐시 유형을 새로 고칠 수도 있습니다.

cli에서 여러 Varnish 인스턴스의 캐시를 새로 고치려면 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 명령으로 명령 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
