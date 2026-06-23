---
title: 바니시로 캐시 지우기
description: Adobe Commerce용 Varnish 웹 캐싱 가속기를 사용하여 캐시 지우기가 작동하는 방식에 대해 알아봅니다. 캐시 관리 및 최적화 기술을 살펴보십시오.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
autotag-review: '2026-06-22T22:18:33.462Z'
TQID: 'https://experienceleague.adobe.com/ePhbVWjx-hX99p8OKiKqzT-w2KZu-XjS1XieuStKqc4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 405
ht-degree: 0%

---

# 바니시로 캐시 지우기

이 항목에서는 Adobe Commerce용 웹 캐싱 가속기로 Varnish를 사용하는 기본 사항에 대해 설명합니다.

{{varnish-config-cloud}}

## 니스 삭제

[Varnish 설명서](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html)에 따르면 &quot;*purge*&#x200B;은(는) 캐시에서 개체를 선택하여 변형과 함께 삭제할 때 발생합니다.&quot; 바니시 제거는 캐시 정리 명령(또는 관리자의 **Magento 캐시 플러시**&#x200B;를 클릭)과 유사합니다.

실제로 Commerce 캐시를 정리하거나 플러시하거나 새로 고치면 바니쉬도 지워집니다.

Commerce에서 작동하도록 Varnish를 설치 및 구성한 후 다음 작업을 통해 Varnish 제거를 수행할 수 있습니다.

- 웹 사이트 유지 관리

  예를 들어, 다음 위치에서 관리에서 수행하는 모든 작업:

   - **스토어** > **설정** > **구성** > 일반 > **일반**
   - **스토어** > **설정** > **구성** > 일반 > **통화 설정**
   - **스토어** > **설정** > **구성** > 일반 > **이메일 주소 저장**

  Commerce에서 이러한 변경 사항을 감지하면 캐시를 새로 고침한다는 메시지가 표시됩니다.

- 스토어 유지 관리(예: 카테고리, 가격, 제품 및 프로모션 요금제 규칙을 추가하거나 편집).

  이러한 작업을 수행하면 바니시가 자동으로 삭제됩니다.

- 소스 코드 유지 관리.

  캐시를 새로 고치고 `generated/code` 및 `generated/metadata` 디렉터리의 모든 항목을 정기적으로 삭제해야 합니다. 캐시 새로 고침에 대한 자세한 내용은 다음 섹션을 참조하십시오.

## 바니시를 제거하도록 Commerce 구성

Commerce은 [`magento setup:config:set`](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset) 명령을 사용하여 Varnish 호스트를 구성한 후 Varnish 호스트를 제거합니다.

선택적 매개 변수 `--http-cache-hosts` 매개 변수를 사용하여 쉼표로 구분된 Varnish 호스트 및 수신 포트 목록을 지정할 수 있습니다. 하나 또는 여러 개의 Vannish 호스트를 모두 구성합니다. ( 공백 문자로 호스트를 구분하지 마십시오.)

매개 변수 형식은 `<hostname or ip>:<listen port>`이어야 합니다. 포트 80인 경우 `<listen port>`을(를) 생략할 수 있습니다.

For example,

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

그런 다음 Admin에서 또는 명령줄을 사용하여 Commerce 캐시(캐시에서 *정리*&#x200B;라고도 함)를 새로 고칠 때 Vannish 호스트를 제거할 수 있습니다.

관리자를 사용하여 캐시를 새로 고치려면 **[!UICONTROL SYSTEM]** > 도구 > **캐시 관리**&#x200B;를 클릭한 다음 페이지 상단의 **Magento 캐시 플러시**&#x200B;를 클릭합니다. 개별 캐시 유형을 새로 고칠 수도 있습니다.

명령줄을 사용하여 캐시를 새로 고치려면 일반적으로 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 명령을 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 사용합니다.
