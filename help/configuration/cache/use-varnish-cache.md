---
title: Varnish를 사용하여 캐시 지우기
description: 캐시 지우기가 Varnish에서 작동하는 방식과 Adobe Commerce 애플리케이션의 웹 캐싱 가속기로 사용하는 방법을 알아봅니다.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# Varnish를 사용하여 캐시 지우기

이 항목에서는 Adobe Commerce 및 Magento Open Source용 웹 캐싱 가속기로 Varnish를 사용하는 기본 사항을 설명합니다.

## 바니쉬 퍼징

에 따라 [Varnish 설명서](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *제거* 에서 객체를 선택하면 [캐시](https://glossary.magento.com/cache) 그리고 그것의 변형과 함께 그것을 버립니다.&quot; Varnish 제거 기능은 캐시 정리 명령과 유사하거나 **플러시 Magento 캐시** ( 관리자).

실제로 상거래 캐시를 정리, 플러시 또는 새로 고치면 Varnish도 삭제됩니다.

Commerce에서 작동하도록 Varnish를 설치 및 구성한 후 다음 작업으로 인해 Varnish 제거가 발생할 수 있습니다.

- 유지 관리 [웹 사이트](https://glossary.magento.com/website).

   예를 들어 의 관리자에서 수행하는 모든 작업:

   - **스토어** > **설정** > **구성** > 일반 > **일반**
   - **스토어** > **설정** > **구성** > 일반 > **통화 설정**
   - **스토어** > **설정** > **구성** > 일반 > **이메일 주소 저장**

   Commerce에서 이러한 변경 사항을 감지하면 캐시를 새로 고치라는 메시지가 표시됩니다.

- 저장소 유지 관리(예: 범주, 가격, 제품 및 판촉 가격 규칙 추가 또는 편집).

   이러한 작업을 수행하면 Varnish가 자동으로 제거됩니다.

- 소스 코드를 유지 관리합니다.

   캐시를 새로 고침하고 `generated/code` 및 `generated/metadata` 디렉토리. 캐시 새로 고침에 대한 자세한 내용은 다음 섹션을 참조하십시오.

## Varnish를 제거하도록 상거래 구성

Commerce에서는 [`magento setup:config:set`](https://devdocs.magento.com/guides/2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) 명령.

선택적 매개 변수를 사용할 수 있습니다 `--http-cache-hosts` 매개 변수를 사용하여 Varnish 호스트 및 수신 포트의 쉼표로 구분된 목록을 지정합니다. 하나 또는 여러 개의 Varnish 호스트를 모두 구성합니다. 공백 문자로 호스트를 분리하지 마십시오.

매개 변수 형식은 다음과 같아야 합니다. `<hostname or ip>:<listen port>`를 생략할 수 있는 위치 `<listen port>` 포트 80이면

For example,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

그런 다음 상거래 캐시를 새로 고칠 때 Varnish 호스트(이라고도 함)를 제거할 수 있습니다 *청소* 캐시)를 지정합니다.

관리자를 사용하여 캐시를 새로 고치려면 **[!UICONTROL SYSTEM]** > 도구 > **캐시 관리**&#x200B;를 클릭한 다음 **플러시 Magento 캐시** 를 클릭합니다. (개별 캐시 유형을 새로 고칠 수도 있습니다.)

명령줄을 사용하여 캐시를 새로 고치려면 일반적으로 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 명령으로 [파일 시스템 소유자](https://devdocs.magento.com/guides/2.4/install-gde/prereq/file-sys-perms-over.html).
