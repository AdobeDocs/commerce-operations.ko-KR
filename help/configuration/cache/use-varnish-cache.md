---
title: 바니시로 캐시 지우기
description: 캐시 지우기가 Varnish에서 작동하는 방식과 Adobe Commerce 애플리케이션의 웹 캐싱 가속기로 사용하는 방법을 알아봅니다.
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 바니시로 캐시 지우기

이 항목에서는 Adobe Commerce 및 Magento Open Source용 웹 캐싱 가속기로 Varnish를 사용하는 기본 사항에 대해 설명합니다.

## 니스 삭제

에 따르면 [니스 설명서](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;a *삭제* 캐시에서 개체를 선택하여 변형과 함께 버리면 어떤 일이 발생합니까?&quot; 바니시 제거는 캐시 정리 명령(또는 클릭)과 유사합니다. **Magento 캐시 초기화** 을 참조하십시오.

실제로 상거래 캐시를 정리하거나 플러시하거나 새로 고치면 바니쉬도 지워집니다.

Varnish를 Commerce와 함께 작동하도록 설치 및 구성한 후 다음 작업을 통해 Varnish를 제거할 수 있습니다.

- 웹 사이트 유지 관리

   예를 들어, 다음 위치에서 관리에서 수행하는 모든 작업:

   - **스토어** > **설정** > **구성** > 일반 > **일반**
   - **스토어** > **설정** > **구성** > 일반 > **통화 설정**
   - **스토어** > **설정** > **구성** > 일반 > **이메일 주소 저장**

   Commerce에서 이러한 변경 사항을 감지하면 캐시를 새로 고침한다는 메시지가 표시됩니다.

- 스토어 유지 관리(예: 카테고리, 가격, 제품 및 프로모션 요금제 규칙을 추가하거나 편집).

   이러한 작업을 수행하면 바니시가 자동으로 삭제됩니다.

- 소스 코드 유지 관리.

   캐시를 새로 고치고 의 모든 항목을 정기적으로 삭제해야 합니다. `generated/code` 및 `generated/metadata` 디렉토리. 캐시 새로 고침에 대한 자세한 내용은 다음 섹션을 참조하십시오.

## 바니시를 제거하도록 Commerce 구성

Commerce는 다음을 사용하여 Varnish 호스트를 구성한 후 Varnish 호스트를 제거합니다. [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) 명령입니다.

선택적 매개 변수를 사용할 수 있습니다 `--http-cache-hosts` 매개 변수를 사용하여 쉼표로 구분된 Varnish 호스트 및 수신 포트 목록을 지정합니다. 하나 또는 여러 개의 Vannish 호스트를 모두 구성합니다. ( 공백 문자로 호스트를 구분하지 마십시오.)

매개 변수 형식은 다음과 같아야 합니다. `<hostname or ip>:<listen port>`, 여기서 을 생략할 수 있습니다. `<listen port>` 80번 포트면

예를 들어,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

그런 다음 Commerce 캐시를 새로 고칠 때 바니시 호스트를 제거할 수 있습니다(이라고도 함) *청소* 캐시)를 관리자 또는 명령줄에서 사용할 수 있습니다.

관리자를 사용하여 캐시를 새로 고치려면 **[!UICONTROL SYSTEM]** > 도구 > **캐시 관리**&#x200B;을 클릭한 다음 을 클릭합니다 **Magento 캐시 초기화** 을 클릭합니다. 개별 캐시 유형을 새로 고칠 수도 있습니다.

명령줄을 사용하여 캐시를 새로 고치려면 일반적으로 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 명령으로 명령 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
