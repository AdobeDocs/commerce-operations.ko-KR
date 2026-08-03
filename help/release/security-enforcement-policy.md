---
title: '보안 정책: 필수 작업 및 기한'
description: 기한, 필수 작업 및 위험을 포함하여 Cloud 버전 및 소프트웨어 종속성에서 지원되지 않는 Adobe Commerce에 대한 보안 강화에 대해 알아봅니다.
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Adobe Commerce on Cloud 전용" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Cloud 버전 2.4.4 - 2.4.9의 Adobe Commerce에만 적용됩니다."
color: blue
source-git-commit: 7cd1bf694234196313373dea6620bdf67e08e82c
workflow-type: tm+mt
source-wordcount: 2017
ht-degree: 0%

---

# 보안 정책: 필수 작업 및 기한

Adobe은 지원되는 소프트웨어 종속성 버전 및 지원되는 Adobe Commerce 버전을 포함하여 클라우드 환경의 Adobe Commerce에 대한 보안 요구 사항을 적용합니다. 이 페이지에서는 필수 사항, 적용 날짜 및 요구 사항이 충족되지 않을 경우 발생하는 상황에 대해 설명합니다.

## 무슨 일이 일어나고 있는 거죠?

Adobe 기업 보안 정책을 사용하려면 Adobe Commerce on Cloud에 대한 모든 Adobe 호스팅 환경이 다음을 포함하여 안전하고 규정을 준수하는 소프트웨어에서 실행되어야 합니다.

1. 모든 타사 소프트웨어 종속성(PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)의 지원되는 버전

1. Adobe Commerce on Cloud의 안전하고 호환 가능한 버전(버전 2.4.8, 2.4.9 또는 최신 버전)

이는 eCommerce 환경에 대한 보안 위험을 완화하기 위한 것입니다. [테이블 1](#determine-your-required-actions)의 기한까지 이러한 요구 사항을 충족하지 않는 환경에서는 인바운드 트래픽이 일시 중단되어 상점 오프라인이 됩니다. 이 알림을 시행일이 포함된 보안 및 규정 준수 요구 사항으로 간주하십시오.

두 가지 작업을 수행해야 할 수 있습니다.

1. 타사 소프트웨어 종속성이 지원되는지 확인합니다. 그렇지 않으면 지원되는 버전으로 업그레이드하십시오.

1. Adobe Commerce on Cloud 버전을 지원되는 버전으로 업그레이드해야 하는지 확인하십시오.

아래에서 Adobe Commerce on Cloud 버전을 찾아 필요한 사항을 확인하고 요구 사항을 확인하십시오.

1. 타사 소프트웨어 종속성

1. Adobe Commerce on Cloud 버전

| 내 버전 | 타사 소프트웨어 종속성 업그레이드<br>(PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)<br>*자세한 내용 및 다음 단계는 [작업 1: 타사 소프트웨어 종속성 업그레이드](#action-1-upgrade-third-party-software-dependencies)를 참조하십시오.* | Adobe Commerce 버전 업그레이드 또는 마이그레이션&#x200B;<br>*자세한 내용 및 다음 단계는 [작업 2: Adobe Commerce on Cloud 버전을 업그레이드해야 하는 경우](#action-2-if-you-need-to-upgrade-your-adobe-commerce-on-cloud-version)를 참조하십시오.* |
| --- | --- | --- |
| 2.4.4 또는 2.4.5 | 2026년 10월 30일까지 필요합니다. | 2027년 6월 1일까지 필요 |
| 2.4.6 또는 2.4.7 | 소프트웨어에 따라 2026년 10월 30일 또는 2027년 5월 31일까지 필요합니다. | 2028년 6월 1일까지 필요 |
| 2.4.8 또는 2.4.9 | 소프트웨어에 따라 2026년 10월 30일 또는 2027년 5월 31일까지 필요합니다. | 지금은 필요하지 않습니다. |

**표 1: 버전별 필수 작업 및 기한**

기한 연장이 필요한 경우 계정 팀이나 [Adobe 지원](https://experienceleague.adobe.com/ko/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)에 문의하십시오.

## 조치를 취할 필요가 없는 사람

이 통지는 다음 경우에 적용되지 않습니다.

* Adobe Commerce on Cloud 버전 2.4.8 또는 2.4.9를 사용하고 환경에서 지원되는 타사 소프트웨어 버전을 실행 중인 고객

* [!DNL Adobe Commerce as a Cloud Service]의 고객

### 실행 중인 버전을 확인하는 방법

실행 중인 버전을 확인하려면 다음 단계를 진행하는 eCommerce 관리자의 도움이 필요합니다.

**Cloud의 Adobe Commerce 버전**

1. Adobe Commerce 관리 패널에 로그인합니다.

   현재 버전은 관리 페이지의 오른쪽 하단에 표시됩니다.

1. 버전이 관리자에 표시되지 않으면 [Adobe Commerce 명령줄 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"}를 사용하여 버전 명령을 실행하십시오.

   ```shell
   bin/magento --version
   ```

**소프트웨어 종속성 버전**

1. [클라우드 콘솔](https://console.adobecommerce.com/)에 로그인합니다.
1. 관련 프로젝트를 연 다음 검토할 환경을 선택합니다.
1. `.magento/services.yaml` 파일에서 해당 환경에 대한 서비스 구성을 확인하십시오. 이 파일은 클라우드 인프라에서 Adobe Commerce에서 사용하는 지원되는 서비스 이름과 버전을 정의합니다.
자세한 지침은 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"} 설명서를 참조하십시오.

## 이 보안 권한이 중요한 이유

공급업체 지원 종료를 통과한 소프트웨어는 더 이상 보안 패치를 받지 않으므로 해당 소프트웨어의 알려진 보안 문제를 해결할 수 없습니다. 또한 [Adobe 라이프사이클 정책](https://experienceleague.adobe.com/ko/docs/commerce-operations/release/planning/lifecycle-policy)에 따라 다음을 수행합니다.

* **Adobe Commerce 버전 2.4.4 및 2.4.5**&#x200B;은(는) 이제 2027년 5월 31일까지 핵심 응용 프로그램에 대해 제한적이고 분리된 보안 수정 사항만 받습니다. 이 제한된 지원에는 품질 수정 사항, 애플리케이션 종속성(예: PHP)에 대한 호환성 지원 또는 플랫폼 종속성 업데이트가 포함되어 있지 않습니다

* **Adobe Commerce 2.4.6**&#x200B;은(는) 2027년 8월 30일까지 확장 지원을 받으며 2028년 5월 31일까지 핵심 응용 프로그램에 대해 제한적이고 격리된 보안 수정만 받습니다

* **Adobe Commerce 버전 2.4.7**&#x200B;은(는) 2027년 5월 31일까지 표준 지원을 받으며 2028년 5월 31일까지 확장 지원을 받게 됩니다.

* **Cloud의 Adobe Commerce 버전 2.4.8 및 2.4.9**&#x200B;은(는) 계속 지원되며 현재 버전을 업그레이드할 필요가 없습니다.

지원되지 않는 소프트웨어에서 전자 상거래 상점을 계속 운영하면 PCI 규정 준수 유지 및 고객 데이터 보호 기능을 포함하여 비즈니스에 실질적인 보안 위험이 증가합니다.

>[!IMPORTANT]
>
>환경이 [표 1](#determine-your-required-actions)에 설명된 기한까지 요구 사항을 충족하지 않으면 Adobe은 영향을 받는 환경에 대한 인바운드 트래픽을 일시 중단합니다. 전자 상거래 상점 첫 페이지는 오프라인으로 전환되며 쇼핑객에게 서비스를 제공하지 않습니다. [아무 작업도 수행되지 않으면 어떻게 되는지](#what-happens-if-no-action-is-taken)를 참조하세요.

## 수행해야 하는 작업에 대한 세부 정보

### 작업 1: 타사 소프트웨어 종속성 업그레이드

소프트웨어에 따라 아래 표에 나와 있는 타임라인을 통해 지원되지 않는 모든 소프트웨어 종속성을 업그레이드해야 합니다. [클라우드 콘솔](https://console.adobecommerce.com/)에서 환경을 보고 이 [지침](#how-to-check-the-versions-you-are-running)을 사용하여 실행 중인 종속성 버전을 확인할 수 있습니다. 소프트웨어 종속성 업그레이드는 Cloud의 모든 Adobe Commerce 버전 2.4.4부터 2.4.9까지 적용됩니다.

| 종속성 | 버전 | 을(를) (으)로 업그레이드해야 함 | 시행일 |
| --- | --- | --- | --- |
| PHP | 8.1 이하 | 8.2 이상 | 2027년 5월 31일 |
| 마리아디비/갈레라 | 10.5 이하 | 10.6 이상 | 2026년 10월 30일 |
| 마리아디비/갈레라 | 10.5보다 크고 10.11보다 작음 | 10.11 이상 | 2027년 5월 31일 |
| Elasticsearch | 모든 버전 | OpenSearch:<br><br>- 2.4.4 및 2.4.5 고객용 버전 2.19<br>- 2.4.6 이상 고객용 버전 3. | 2026년 10월 30일 |
| OpenSearch | 1.x | 2.4.4 및 2.4.5 고객용 버전 2.19.<br>2.4.6 이상 고객용 버전 3. | 2027년 5월 31일 |
| 레디스 | 5 이하 | Valkey 8 이상 | 2027년 5월 31일 |
| 래빗MQ | 3.9 이하 | 3.13 이상 | 2026년 10월 30일 |
| 래빗MQ | 3.9보다 크고 3.13보다 작음 | 4.3 이상 | 2027년 5월 31일 |

**표 2: 소프트웨어 종속성 업그레이드 요구 사항**

#### 타사 소프트웨어 종속성 업그레이드 준비

Adobe은 이러한 소프트웨어 종속성을 직접 업그레이드하는 데 도움이 됩니다.

* **시작하기:** 업그레이드해야 하는 환경과 관련된 종속성을 나열하는 [지원 티켓을 엽니다](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide). 우리 팀이 작업 일정을 잡을 수 있도록 시행 날짜 최소 30일 전에 티켓을 여십시오.

* **가동 중지 시간:** Adobe에서 예약할 때 필요한 기간을 확인합니다.

* **테스트:** 프로덕션하기 전에 비프로덕션 환경을 업그레이드하고 유효성을 검사합니다. 최소한 체크아웃, 검색, 장바구니 및 모든 사용자 정의 통합의 유효성을 검사하십시오. 요구 사항은 모든 환경에 적용되므로 프로덕션 환경만 업그레이드하지 않고 모든 환경을 업그레이드하도록 계획하십시오.

* **호환성:** 이러한 변경 사항 중 대부분은 동일한 소프트웨어 내에서 버전을 업그레이드하는 것이며 위험성이 낮습니다. 다음은 더욱 세심한 주의를 기울일 것을 보증합니다.

  * **Elasticsearch에서 OpenSearch로** 및 **Redis에서 Valkey로**&#x200B;이(가) 버전 업그레이드가 아닌 다른 소프트웨어로 마이그레이션되고 있습니다. 원본 서비스를 참조하는 사용자 지정 코드, 확장 또는 구성을 업데이트해야 할 수 있습니다.
  * **PHP 8.1 ~ 8.2**&#x200B;은(는) 사용자 지정 코드 및 타사 확장에서 더 이상 사용되지 않습니다.

서드파티 확장을 사용하는 경우 확장 공급업체에 현재 릴리스가 타겟 버전을 지원하는지 확인합니다. 솔루션 통합자와 협력하는 경우 계획 및 유효성 검사에 해당 통합자를 참여시킵니다.

### 작업 2: Adobe Commerce on Cloud 버전을 업그레이드해야 하는 경우:

(i) 지원되는 Adobe Commerce on Cloud 버전으로 업그레이드하거나 (ii) Adobe Commerce as a Cloud Service(Adobe의 전체 관리 상거래 플랫폼)로 마이그레이션할 수 있습니다

현재 버전에 대한 적용 날짜는 선택한 옵션에 관계없이 적용됩니다.

| 현재 버전 | 액션 | 시행일 |
| --- | --- | --- |
| Cloud 버전 2.4.4 또는 2.4.5에서 Adobe Commerce 사용 | Cloud 버전 2.4.9(또는 최신 버전)의 Adobe Commerce으로 업그레이드하거나 Adobe Commerce as a Cloud Service으로 마이그레이션하십시오. | 2027년 6월 1일 |
| Cloud 버전 2.4.6 또는 2.4.7에서 Adobe Commerce 사용 | Cloud 버전 2.4.9(또는 최신 버전)의 Adobe Commerce으로 업그레이드하거나 Adobe Commerce as a Cloud Service으로 마이그레이션하십시오. | 2028년 6월 1일 |
| Cloud 버전 2.4.8 또는 2.4.9에서 Adobe Commerce 사용 | 현재 Adobe Commerce on Cloud 버전 업그레이드 작업이 필요하지 않습니다. 작업 1의 소프트웨어 종속성 기한이 여전히 적용됩니다. | 해당 사항 없음 |

**표 3: Cloud에서 현재 Adobe Commerce 버전을 업그레이드해야 하는 경우의 지침 및 기한**

Adobe Commerce on Cloud 버전 2.4.9 및 Adobe Commerce as a Cloud Service에 대한 자세한 내용은 다음 표를 참조하십시오.

**표 4: Cloud의 Adobe Commerce으로 업그레이드 대 Adobe Commerce as a Cloud Service으로 마이그레이션**

| | Adobe Commerce on Cloud 버전 2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| 정의 | 전체 보안 적용 범위, 품질 수정 및 플랫폼 종속성 업데이트가 포함된 최신 Adobe Commerce 릴리스입니다. | 업그레이드 오버헤드 없이 지속적인 혁신을 위해 구축된 Adobe의 완전 관리 상거래 플랫폼. [자세히 알아보기](https://experienceleague.adobe.com/ko/docs/commerce/cloud-service/overview) |
| 다음과 같은 경우에 적합합니다. | 현재로서는 인프라, 업그레이드 및 패치를 계속 관리해야 합니다. 준비되면 언제든지 Adobe Commerce as a Cloud Service으로 마이그레이션할 수 있습니다. | 업그레이드 주기를 길게 두어 총소유비용을 절감하고 Adobe의 최신 기능을 별도의 노력 없이 자동으로 제공하고자 합니다. |
| 주요 이점 | 기존 설정을 유지하면서 보안 요구 사항을 충족합니다. | 번개처럼 빠른 에지 전송 상점, 확장성이 뛰어난 카탈로그, 기본 디지털 에셋 관리 및 내장된 생성 AI를 Adobe에서 관리하는 인프라에 탑재합니다. |

## 아무 조치도 취하지 않으면 어떻게 됩니까?

환경이 공유된 적용 날짜 [이상](#determine-your-required-actions)까지 이러한 요구 사항을 충족하지 않으면 Adobe에서 적절한 조치를 취합니다. 여기에는 영향을 받는 인프라에 대한 트래픽 일시 중지가 포함되며, 그 결과 eCommerce 상점 오프라인이 발생합니다.

트래픽 일시 중단 후에도 환경이 계속 규정을 준수하지 않는 경우 Adobe이 클라우드 서비스를 종료하여 서비스 해제 프로세스를 시작할 수 있습니다. 서비스 해제의 결과로 모든 인스턴스, 환경 및 분기를 포함하여 호스트된 eCommerce 환경 내의 모든 데이터 및 에셋은 영구적으로 삭제되며 복원할 수 없습니다.

## Adobe이 제공하는 이점 요약

Adobe은 업그레이드든 마이그레이션이든 간에 최대한 원활하게 전환할 수 있는 도구와 지원을 제공합니다.

**Cloud 버전 2.4.9에서 Adobe Commerce으로 업그레이드하도록 선택한 경우**

* **업그레이드 호환성 보고서:** Adobe은 시간 및 비용 범위를 포함하여 Adobe Commerce 버전 2.4.9로 업그레이드하는 데 필요한 사항을 정확히 식별하는 자세한 보고서를 제공합니다. [업그레이드 호환성 보고서를 생성합니다](https://supportinsights.adobe.com/commerce/tab/main).

* **소프트웨어 종속성 업그레이드:** 소프트웨어 종속성을 직접 업그레이드할 수 없으므로 Adobe에 대한 [지원 티켓을 여십시오](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide){target="_blank"}. 업그레이드를 처리하십시오. 자세한 내용은 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}을 참조하세요.

**Adobe Commerce as a Cloud Service으로 마이그레이션하기로 선택한 경우**

Adobe은 Adobe Commerce as a Cloud Service으로 마이그레이션하는 데 드는 비용과 시간을 줄이는 도구를 제공합니다. 이것은 당신에게 아무 비용도 들지 않습니다. 이러한 도구는 마이그레이션에만 적용되며 Cloud의 Adobe Commerce에서 버전을 업그레이드하는 데 사용되지 않습니다. 마이그레이션 경로 및 단계를 포함한 전체 마이그레이션 가이드는 [마이그레이션 개요](https://experienceleague.adobe.com/ko/docs/commerce/cloud-service/migration/overview)를 참조하십시오.

* **마이그레이션 평가:** 사용자 지정의 마이그레이션 복잡성을 평가합니다. [마이그레이션 평가 도구 개요](https://experienceleague.adobe.com/ko/docs/commerce/cloud-service/migration/migration-tools/assessment)를 참조하세요.

* **데이터 마이그레이션:** [대량 및 증분 데이터 마이그레이션 도구](https://experienceleague.adobe.com/ko/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)가 데이터를 새 Adobe Commerce as a Cloud Service 환경으로 이동합니다.

* **[!DNL Adobe Developer App Builder]** 및 **[!DNL Commerce Storefront powered by Edge Delivery Services]**&#x200B;을(를) 포함한 Adobe의 [AI 지원 마이그레이션 및 개발자 도구](https://developer.adobe.com/commerce/extensibility/developer-agent/)은(는) 상점 현대화 및 확장 플랫폼 재구성을 가속화하는 데 도움이 됩니다.

질문이 있는 경우 계정 팀, 솔루션 계정 관리자, 갱신 전문가에게 문의하거나 [지원 서비스](https://experienceleague.adobe.com/ko/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)에 문의하십시오.
