---
title: 서비스 구성 경로 참조
description: Adobe Commerce 관리 설정에서 서비스 구성 경로 및 값에 대해 알아봅니다. 웹 API, OAuth 및 서비스 통합 구성 옵션을 살펴보십시오.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# 서비스 구성 경로 참조

이 섹션에는 **스토어** > 설정 > **구성** > **서비스**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

[`magento app:config:dump` 명령](../cli/export-configuration.md)은(는) 이러한 값을 소스 제어에 있어야 하는 공유 구성 파일 `app/etc/config.php`에 씁니다. 선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 [환경 변수를 사용하여 구성 설정을 무시하십시오](override-config-settings.md#environment-variables). 이 항목은 _not_&#x200B;에 [중요 및 시스템 특정 값을 나열합니다](config-reference-sens.md).

## Commerce 웹 API 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **서비스** > **웹 API**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| 기본 응답 문자 집합 | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 익명 게스트 액세스 허용 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **서비스** > **OAuth**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| 고객 토큰 라이프타임(시간) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리 토큰 라이프타임(시간) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정리 확률 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 만료 기간 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 만료 기간 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth 소비자 자격 증명 HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth 소비자 자격 증명 HTTP Post 시간 초과 | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
