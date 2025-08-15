---
title: 여러 Varnish 인스턴스를 사용하여 캐시 지우기
description: 여러 Varnish 인스턴스에서 캐시 지우기가 작동하는 방식을 알아봅니다.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# 여러 Varnish 인스턴스를 지우는 캐시

Adobe Commerce은 즉시 여러 Vannish 인스턴스를 지원합니다.

이 항목에서는 Commerce으로 여러 가지 바니시 인스턴스를 구성하는 기본 사항을 보여줍니다.

## 여러 Varnish 인스턴스를 제거하는 구성

Commerce은 [`magento setup:config:set`](../../installation/tutorials/deployment.md) 명령을 사용하여 Varnish 호스트를 구성한 후 Varnish 호스트를 제거합니다.

`--http-cache-hosts` 매개 변수를 사용하여 쉼표로 구분된 Varnish 호스트 및 수신 포트 목록을 지정해야 합니다. ( 공백 문자로 호스트를 구분하지 마십시오.)

매개 변수 형식은 `<hostname or ip>:<listen port>`이어야 합니다. 포트 80인 경우 `<listen port>`을(를) 생략할 수 있습니다.

For example,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

그런 다음 Admin에서 또는 명령줄을 사용하여 Commerce 캐시(캐시에서 _정리_&#x200B;라고도 함)를 새로 고칠 때 모든 Vannish 호스트를 제거할 수 있습니다.

관리자를 사용하여 캐시를 새로 고치려면 **시스템** > 도구 > **캐시 관리**&#x200B;를 클릭한 다음 페이지 상단에서 **Magento 캐시 플러시**&#x200B;를 클릭합니다. 개별 캐시 유형을 새로 고칠 수도 있습니다.

cli에서 여러 Varnish 인스턴스의 캐시를 새로 고치려면 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 명령을 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 사용합니다.
