---
title: Commerce 환경을 보호하기 위해 필요한 작업 및 기한
description: 기한, 필수 작업 및 위험을 포함하여 Cloud 버전 및 소프트웨어 종속성에서 지원되지 않는 Adobe Commerce에 대한 보안 강화에 대해 알아봅니다.
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: cc250cf1-34eb-4863-80d0-d170d45ea067id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Cloud 2.4.4 - 2.4.9의 Adobe Commerce 전용" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Cloud 버전 2.4.4 - 2.4.9의 Adobe Commerce에만 적용됩니다."
nudge: true
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: 2158
ht-degree: 0%

---


# Commerce 환경을 보호하기 위해 필요한 작업 및 기한

>[!NOTE]
>
> **적용 대상:** Adobe Commerce 버전 2.4.4 - 2.4.9를 실행하는 PaaS(Adobe Commerce on Cloud) 환경.

사이버 보안 환경은 근본적으로 변화하고 있으며, 기업들이 갖추어야 할 방어 메커니즘은 빠르게 발전해야 합니다. 전자 상거래 기업은 온라인 거래를 통해 민감한 개인 및 비즈니스 데이터를 처리해야 하므로 보안이 매우 중요합니다. PaaS 전자 상거래 환경에는 애플리케이션 계층 종속성의 보안 및 유지 관리, 타사 소프트웨어와의 통합, 배포 파이프라인을 고객이 담당하는 공유 책임 모델이 있습니다.

Adobe에서는 계속 변화하는 위험을 해결하고 Adobe Commerce on Cloud 고객을 가장 높은 보안 표준으로 설정할 수 있도록 최선을 다하고 있습니다. 여기에는 다음이 포함됩니다.

1. 중요한 취약점에 대해 빠르고 예측 가능한 보호를 위해 매월 격리되는 보안 수정

2. 클라우드 환경과의 통합을 개선하고 중요한 문제를 신속하게 해결할 수 있는 Adobe 패치 및 핫픽스를 확실하게 제공하는 Commerce용 클라우드 패치 패키지

3. 라이프사이클 적용 정책

4. 필요한 경우 사이클 핫픽스 제외

5. 장기 지원이 포함된 연간 패치 릴리스


Adobe은 고객을 안전하게 보호하는 데 필요한 단계를 수행하지만 Adobe Commerce on Cloud에 대한 공유 책임 모델은 고객이 항상 지원되는 버전의 Adobe Commerce on Cloud 및 타사 소프트웨어를 사용하고 있어야 하며, 애플리케이션 패치를 적용하고, 타사 확장을 감사하고, 사용자 정의 코드를 보호해야 합니다. 공급업체 지원 종료를 통과한 소프트웨어는 더 이상 보안 패치를 받지 않으므로 소프트웨어의 보안 문제가 해결되지 않습니다. 지원되지 않는 소프트웨어에서 전자 상거래 저장소를 계속 실행하면 보안 위험이 점점 커지고 있습니다.

이 페이지에서는 전자 상거래 환경을 안전하게 유지하기 위해 Adobe Commerce on Cloud(버전 2.4.4 ~ 2.4.9)의 모든 고객이 수행해야 하는 작업과 시행 날짜, 보안 요구 사항이 충족되지 않을 때 예상할 사항에 대해 설명합니다.

## 보안 및 규정 준수 환경을 유지 관리하는 데 필요한 작업

전자 상거래 환경을 안전하게 유지하고 위험을 완화하려면 Adobe Commerce on Cloud(버전 2.4.4 ~ 2.4.9)의 모든 고객은 다음을 사용해야 합니다.

1. 모든 타사 소프트웨어 종속성(PHP, MariaDB, Elasticsearch, OpenSearch, Redis, RabbitMQ)의 지원되는 버전

1. 클라우드에서 안전하고 지원되는 Adobe Commerce 버전입니다. 완전히 지원되는 버전에는 2.4.8, 2.4.9 또는 사용 가능한 최신 릴리스가 포함됩니다. [라이프사이클 정책](/help/release/lifecycle-policy.md) 설명서를 참조하세요.

클라우드 환경에서 Adobe Commerce을 보호하기 위해 조치를 취해야 하는지 확인하려면 아래 지침을 따르십시오. 아래 표 1에 요약된 기한까지 보안 요구 사항을 충족하지 않는 환경에서는 인바운드 트래픽이 중단되어 스토어프런트가 오프라인 상태가 됩니다. 기한 충족에 대해 우려되는 경우 가능한 한 빨리 계정 팀이나 [Adobe 지원](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)에 문의하십시오.

>[!NOTE]
>
> 이 지침은 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(SaaS) 환경 또는 Adobe Commerce 온-프레미스 배포에는 적용되지 않습니다.

**표 1: 보안 요구 사항 및 기한**

| Adobe Commerce on Cloud 버전 | 지원되는 타사 소프트웨어 종속성으로 업그레이드 | Cloud 버전의 최신 Adobe Commerce으로 업그레이드하거나 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션하십시오. |
| --- | --- | --- |
| 2.4.4 또는 2.4.5 | 2026년 10월 30일까지 필요합니다. | 2027년 6월 1일까지 필요 |
| 2.4.6 또는 2.4.7 | 소프트웨어에 따라 2026년 10월 30일 또는 2027년 5월 31일까지 필요합니다. | 2028년 6월 1일까지 필요 |
| 2.4.8 또는 2.4.9 | 소프트웨어에 따라 2026년 10월 30일 또는 2027년 5월 31일까지 필요합니다. | 지금은 필요하지 않습니다. |

## 환경 보호를 위한 자세한 단계

Commerce 관리자에게 문의하여 다음 단계를 수행하십시오.

### 작업 1: 타사 소프트웨어 종속성 확인 및 업그레이드

사용자 환경에서 PHP, MariaDB, Elasticsearch, OpenSearch, Redis, RabbitMQ와 같은 타사 소프트웨어 종속성에 대해 공급업체가 지원하는 버전을 실행하고 있는지 확인합니다. 그렇지 않으면 소프트웨어 종속성을 지원되는 버전으로 업그레이드하십시오.

#### 1단계: 타사 소프트웨어 종속성 버전 확인

1. 모든 클라우드 프로젝트를 볼 수 있는 [클라우드 콘솔](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/start/cloud-console)에 로그인합니다.
2. 관련 프로젝트를 연 다음 검토할 환경을 선택합니다.
3. 선택한 환경에서 현재 사용 중인 모든 서비스 목록을 볼 수 있는 &quot;컨테이너&quot; 탭을 엽니다.
4. 각 서비스 링크를 클릭하여 현재 환경에서 실행 중인 정확한 버전을 확인합니다.
자세한 내용은 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)의 지침을 참조하십시오.

지원되지 않는 모든 소프트웨어 종속성은 아래 표 2에 나와 있는 타임라인으로 요약된 버전으로 업그레이드해야 합니다.

**표 2: 필요한 종속성 업그레이드**

| 종속성 | 버전 | 을(를) (으)로 업그레이드해야 함 | 기한 |
| --- | --- | --- | --- |
| PHP | 8.1 이하 | 8.2 이상 | 2027년 5월 31일 |
| 마리아디비/갈레라 | 10.5 이하 | 10.6 이상 | 2026년 10월 30일 |
| 마리아디비/갈레라 | 10.5보다 크고 10.11보다 작음 | 10.11 이상 | 2027년 5월 31일 |
| Elasticsearch | 모든 버전 | OpenSearch: 버전 2.19(2.4.4 및 2.4.5 고객용) 버전 3 - 2.4.6 이상 고객 | 2026년 10월 30일 |
| OpenSearch | 1.x | 버전 2.4.4 및 2.4.5 고객용. 버전 3 - 2.4.6 이상 고객 | 2027년 5월 31일 |
| 레디스 | 5 이하 | 버전 8 이상 유효성 검사 | 2027년 5월 31일 |
| 래빗MQ | 3.9 이하 | 버전 3.13 이상 | 2026년 10월 30일 |
| 래빗MQ | 3.9보다 크고 3.13보다 작음 | 4.3 이상 | 2027년 5월 31일 |

#### 2단계: 타사 소프트웨어 종속성 업그레이드 준비

Adobe은 이러한 소프트웨어 종속성을 직접 업그레이드하는 데 도움이 됩니다.

* **시작하기:** 업그레이드해야 하는 환경과 관련된 종속성을 나열하는 [지원 티켓을 엽니다](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case). Adobe에서 작업을 예약할 수 있도록 적어도 시행일 30일 전에 티켓을 엽니다.

* **가동 중지 시간:** Adobe에서 예약할 때 필요한 기간을 확인합니다.

* **테스트:** 프로덕션하기 전에 비프로덕션 환경을 업그레이드하고 유효성을 검사합니다. 최소한 체크아웃, 검색, 장바구니 및 모든 사용자 정의 통합의 유효성을 검사하십시오. 요구 사항은 모든 환경에 적용되므로 프로덕션 환경만 업그레이드하지 않고 모든 환경을 업그레이드하도록 계획하십시오.

* **호환성:** 이러한 변경 사항 중 대부분은 동일한 소프트웨어 내에서 버전을 업그레이드하는 것이며 위험성이 낮습니다. 다음 변경은 더욱 세심한 주의를 요합니다.

  * **Elasticsearch에서 OpenSearch로** 및 **Redis에서 Valkey로**&#x200B;이(가) 버전 업그레이드가 아닌 다른 소프트웨어로 마이그레이션되고 있습니다. 원본 서비스를 참조하는 사용자 지정 코드, 확장 또는 구성은 업데이트가 필요할 수 있습니다.
  * **PHP 8.1에서 8.2**(으)로 업그레이드하면 사용자 지정 코드 및 타사 확장에서 사용이 중단됩니다.

서드파티 확장을 사용하는 경우 공급업체에 현재 릴리스가 타겟 버전을 지원하는지 확인하십시오. 솔루션 통합자와 협력하는 경우 계획 및 유효성 검사에 해당 통합자를 참여시킵니다.

### 작업 2: Adobe Commerce on Cloud 버전 확인 및 지원되는 버전으로 업그레이드

#### 1단계: Adobe Commerce on Cloud 버전 및 필요한 작업 확인

1. Adobe Commerce 관리 패널에 로그인합니다.

   현재 버전은 관리 페이지의 오른쪽 하단에 표시됩니다.

1. 버전이 관리 패널에서 숨겨져 있는 경우 다음 명령을 실행하여 Adobe Commerce [명령줄 도구](../configuration/cli/config-cli.md)를 사용하여 버전을 확인하세요.

   ```shell
   bin/magento --version
   ```

아래 표에서 사용 중인 Adobe Commerce 버전에 대한 필수 작업을 확인하십시오.

**표 3: Adobe Commerce on Cloud 버전 업그레이드 요구 사항**

| 클라우드에 있는 Adobe Commerce의 현재 버전 | 필수 작업 | 기한 |
| --- |--- |--- |
| 버전 2.4.4 또는 2.4.5 | Cloud 버전 2.4.9(또는 최신 버전)의 Adobe Commerce으로 업그레이드하거나 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션하십시오.<br>이유: 버전 2.4.4 및 2.4.5에는 2027년 5월 31일까지 핵심 응용 프로그램에 대한 제한적이고 격리된 보안 수정만 제공됩니다. 여기에는 품질 수정 사항, 애플리케이션 종속 항목에 대한 호환성 지원(예: PHP) 또는 플랫폼 종속 업데이트가 포함되지 않습니다. Adobe의 [라이프사이클 정책](/help/release/lifecycle-policy.md)을 참조하세요. | 2027년 6월 1일 |
| 버전 2.4.6 또는 2.4.7 | Cloud의 Adobe Commerce 버전 2.4.9(또는 최신 버전)로 업그레이드하거나 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션하십시오.<br>이유: 버전 2.4.6은 2027년 8월 30일까지 확장 지원을 받으며 2028년 5월 31일까지 핵심 응용 프로그램에 대한 제한적이고 격리된 보안 수정만 받습니다. 버전 2.4.7은 2027년 5월 31일까지 표준 지원을 받고 2028년 5월 31일까지 확장 지원을 받게 됩니다. Adobe의 [라이프사이클 정책](/help/release/lifecycle-policy.md)을 참조하세요. | 2028년 6월 1일 |
| 버전 2.4.8 또는 2.4.9 | Adobe Commerce on Cloud 버전 업그레이드 작업은 필요하지 않습니다. 작업 1의 타사 소프트웨어 종속성 기한이 여전히 적용됩니다.<br>이유: 기한이 설정되지 않았습니다. | 해당 사항 없음 |

#### 2단계: 업그레이드 또는 마이그레이션 경로 결정

Adobe Commerce on Cloud 버전을 업그레이드해야 하는 경우 두 가지 옵션이 있습니다.

1. 지원되는 클라우드 기반 Adobe Commerce 버전으로 업그레이드
1. [!DNL Adobe Commerce as a Cloud Service]&#x200B;(SaaS)로 마이그레이션

다음 표는 옵션을 비교하고 최적의 경로를 결정하는 데 도움이 됩니다.

**표 4:[!DNL Adobe Commerce as a Cloud Service]**&#x200B;과(와) 비교하여 클라우드의 Adobe Commerce

| | Adobe Commerce on Cloud 버전 2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **내용** | 전체 보안 적용 범위, 품질 수정 및 플랫폼 종속성 업데이트가 포함된 최신 Adobe Commerce 릴리스입니다. | 업그레이드 오버헤드 없이 지속적인 혁신을 위해 구축된 Adobe의 완전 관리 상거래 플랫폼. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview) |
| **가장 적합한 경우** | 고유한 인프라, 업그레이드 및 패치를 계속 관리하려는 경우 | 업그레이드 주기를 길게 두어 총소유비용을 절감하고 Adobe의 최신 기능을 별도의 노력 없이 자동으로 제공하고자 합니다. |
| **주요 이점** | 기존 설정을 유지하면서 보안 요구 사항을 충족합니다. | 번개처럼 빠른 에지 전송 상점, 확장성이 뛰어난 카탈로그, 기본 디지털 에셋 관리 및 내장된 생성 AI를 Adobe에서 관리하는 인프라에 탑재합니다. |

## 기한까지 조치를 취하지 않으면 어떻게 됩니까?

Adobe은 지원되는 타사 소프트웨어 버전을 채택하거나, Cloud에서 Adobe Commerce의 최신 버전으로 업그레이드하거나, Adobe Commerce as a Cloud Service으로 마이그레이션하는 데 필요한 단계를 실행하는 데 사용자를 지원하기 위해 최선을 다하고 있습니다.  기한 충족에 대한 우려가 있고 짧은 연장이 필요한 경우 가능한 한 빨리 계정 팀이나 [Adobe 지원](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)에 문의하십시오.

위에서 공유한 시행 날짜까지 환경이 보안 요구 사항을 충족하지 않으면 Adobe은 Adobe Commerce 플랫폼 및 고객의 보안을 유지하기 위해 적절한 조치를 취하지 않을 수 없습니다. 여기에는 영향을 받는 인프라에 대한 트래픽 일시 중지가 포함되며, 그 결과 Commerce 상점 첫 페이지는 오프라인으로 전환됩니다.

트래픽 일시 중단 후에도 환경이 계속 규정을 준수하지 않는 경우 Adobe이 클라우드 서비스를 종료하여 서비스 해제 프로세스를 시작할 수 있습니다. 서비스 해제의 결과로 모든 인스턴스, 환경 및 분기를 포함하여 호스팅된 상거래 환경 내의 모든 데이터 및 자산은 영구적으로 삭제되며 복원할 수 없습니다.

## 업그레이드 또는 마이그레이션을 지원하는 리소스

**Cloud 버전 2.4.9에서 Adobe Commerce으로 업그레이드하도록 선택한 경우:**

* **업그레이드 호환성 보고서:** Adobe은 업데이트가 필요한 모듈 및 파일, 중요한 문제 수 등을 포함하여 Adobe Commerce 버전 2.4.9로 업그레이드하는 데 필요한 사항을 정확히 식별하는 자세한 보고서를 제공합니다. 업그레이드 호환성 보고서를 생성하는 방법에 대한 자세한 내용은 [사이트 전체 분석 도구](/help/tools/site-wide-analysis-tool/access.md) 설명서를 참조하십시오.

* **소프트웨어 종속성 업그레이드:** 소프트웨어 종속성을 직접 업그레이드할 수 없으므로 Adobe에서 [지원 티켓](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)을 열어 업그레이드를 처리하십시오. 자세한 내용은 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)을 참조하세요.

**[!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션하도록 선택한 경우:**

Adobe은 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션하는 데 드는 비용과 시간을 줄이는 도구를 제공합니다. 이 제품들은 무료로 제공됩니다. 이 도구는 마이그레이션에만 적용됩니다. Adobe Commerce on Cloud 버전 업그레이드에는 사용되지 않습니다. 마이그레이션 경로 및 단계를 포함한 전체 마이그레이션 가이드는 [마이그레이션 개요](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview)를 참조하십시오.

* **마이그레이션 평가:** 사용자 지정의 마이그레이션 복잡성을 평가합니다. [마이그레이션 평가 도구 개요](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment)를 참조하세요.

* **데이터 마이그레이션:** [대량 및 증분 데이터 마이그레이션 도구](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)가 데이터를 새 [!DNL Adobe Commerce as a Cloud Service] 환경으로 이동합니다. 액세스하려면 [Adobe 지원](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)에 문의하십시오.

* **AI 지원 마이그레이션 및 개발자 도구:** Edge Delivery Services에서 제공하는 Adobe Developer App Builder 및 Commerce Storefront를 통해 Storefront 현대화 및 확장 재플랫폼을 가속화할 수 있습니다.

질문이 있는 경우 계정 팀에 문의하거나 [지원 서비스](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)에 문의하십시오.

>[!MORELIKETHIS]
>
>* [라이프사이클 정책](lifecycle-policy.md)
>* [Cloud의 Adobe Commerce에 대한 버전 업그레이드 시행 정책](version-upgrade-enforcement-policy.md)
>* [공유 권한 보안 및 운영 모델](../security-and-compliance/shared-responsibility.md)
