---
title: 서비스 구성 경로 참조
description: 서비스 구성 값 목록을 참조하십시오.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# 서비스 구성 경로 참조

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **서비스**.

다음 [`magento app:config:dump` 명령](../cli/export-configuration.md) 이 값을 공유 구성 파일에 씁니다. `app/etc/config.php`: 소스 제어에서 사용해야 합니다. 선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 다음을 참조하십시오 [환경 변수를 사용하여 구성 설정 무시](override-config-settings.md#environment-variables). 이 주제의 기능은 다음과 같습니다 _not_ list [구분 및 시스템 특정 값](config-reference-sens.md).

## 상거래 웹 API 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **서비스** > **웹 API**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 기본 응답 문자 세트 | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 익명 게스트 액세스 허용 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## OAuth 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **서비스** > **OAuth**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 고객 토큰 라이프타임(시간) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리 토큰 라이프타임(시간) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정리 가능성 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 만료 기간 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 만료 기간 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth 소비자 자격 증명 HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth 소비자 자격 증명 HTTP Post 시간 제한 | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
