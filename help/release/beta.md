---
title: Beta 릴리스
description: Adobe Commerce 베타 릴리스와 참여 방법에 대해 알아봅니다.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: d467ada97a81d64dff358bc83acd489f69ba0677
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 0%

---

# Adobe Commerce 베타 릴리스

Adobe Commerce 베타 프로그램은 판매자가 프리릴리스 기능과 코드에 액세스하고, 피드백을 제공하고, Adobe Commerce의 미래를 안내할 수 있는 방법입니다. 베타 프로그램에는 두 가지 유형이 있습니다.

- 공개 Beta: 공개 베타 프로그램은 모든 Adobe Commerce 고객 및 파트너가 사용할 수 있습니다
- Private Beta: 비공개 베타 프로그램에 참여하려면 자격 기준에 따른 승인이 필요할 수 있습니다

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 등을 통해)할 의무가 없습니다. 고객은 베타 릴리스 및/또는 관련 설명서나 자료의 올바른 기능이나 성능에 어떠한 의존도 하지 말고 주의하는 것이 좋습니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

## 참여의 이점

Adobe이 개발 중인 기능에 일찍 액세스하면 고객과 파트너가 피드백을 제공하고 제품 개발을 구체화하며 일반 출시 전에 새로운 기능을 채택할 수 있습니다.

## 최신 Beta 프로그램

활성 베타 프로그램 목록은 다음 섹션을 참조하십시오.

### Cloud Automation 패치 서비스(Private Beta)

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)는 [Cloud Infrastructure의 Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview) 환경에 격리된 보안 패치를 적용하는 프로세스를 자동화합니다.

2025년 10월에 Cloud Automation 패치 서비스의 베타 릴리스가 [사이트 전체 분석 도구 대시보드](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard)에 추가됩니다. 이 서비스는 다음과 같은 작업을 포함하는 간소화된 패치 작업 과정을 통해 Commerce 프로젝트 관리자를 지원합니다.

- 자동 패치 설치
- 롤백 복구
- 배포 후 확인.

이 서비스를 사용하면 최소한의 수고와 위험으로 안전하고 안정적이며 업데이트된 환경을 유지할 수 있습니다.

Beta에는 다음 기능이 포함되어 있습니다.

- **패치 설치 자동화**: 여러 환경에서 중요한 취약점을 패치하는 프로세스를 단순화하고 자동화합니다.
- **위험 최소화**: 배포 후 상태 확인 및 롤백 기능을 통해 사이트 중단을 방지합니다.

>[!NOTE]
>
>Cloud Automation Patching Service는 격리된 보안 패치를 자동으로 적용하므로 이를 사용하려면 [기여자 또는 프로젝트 관리자 역할](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access)이 있어야 합니다.

이 Beta에 참여하려면 [Cloud Automation 패치 서비스 - Beta 등록 양식](https://forms.office.com/r/3Wfxj5nPdB)을 완료하고 제출하십시오.

### 라이브 검색에 대한 검색 기능 향상(공개 Beta)

이 베타는 [`productSearch` 쿼리](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/)에서 세 가지 새로운 기능을 지원합니다.

- **계층화된 검색** - 다른 검색 컨텍스트에서 검색 - 이 기능을 사용하면 검색 쿼리에 대해 최대 두 개의 계층을 검색할 수 있습니다. For example:

   - **계층 1 검색** - &quot;product_attribute_1&quot;에서 &quot;motor&quot;를 검색합니다.
   - **계층 2 검색** - &quot;product_attribute_2&quot;에서 &quot;부품 번호 123&quot;을 검색합니다. 이 예제에서는 결과 내에서 &quot;motor&quot;에 대해 &quot;part number 123&quot;을 검색합니다.

  아래에 설명된 대로 `startsWith` 검색 인덱싱과 `contains` 검색 인덱싱에 모두 계층화된 검색을 사용할 수 있습니다.

- **검색 인덱싱으로 시작** - `startsWith` 인덱싱을 사용하여 검색 이 새로운 기능을 통해 다음과 같은 작업을 수행할 수 있습니다.

   - 속성 값이 특정 문자열로 시작하는 제품을 검색합니다.
   - 구매자가 속성 값이 특정 문자열로 끝나는 제품을 검색할 수 있도록 &quot;다음으로 끝남&quot; 검색을 구성합니다. &quot;다음으로 끝남&quot; 검색을 활성화하려면 제품 속성을 역순으로 수집해야 하며 API 호출도 역순 문자열이어야 합니다.

- **검색 인덱싱을 포함** -포함 인덱싱을 사용하여 특성을 검색합니다. 이 새로운 기능을 통해 다음과 같은 작업을 수행할 수 있습니다.

   - 더 큰 문자열 내에서 쿼리를 검색하고 있습니다. 예를 들어 구매자가 문자열 &quot;HAPE-123&quot;에서 제품 번호 &quot;PE-123&quot;을 검색하는 경우,

     >[!NOTE]
     >
     >이 검색 유형은 자동 완성 검색을 수행하는 기존 [구 검색](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/)과(와) 다릅니다. 예를 들어 제품 속성 값이 &quot;outdoor pants&quot;인 경우 구문 검색은 &quot;out pan&quot;에 대한 응답을 반환하지만 &quot;or ants&quot;에 대한 응답은 반환하지 않습니다. 그러나 에는 검색이 포함되어 있으며 &quot;or ants&quot;에 대한 응답을 반환합니다.

이러한 새 조건은 검색 결과를 구체화하기 위한 검색 쿼리 필터링 메커니즘을 향상시킵니다. 이러한 새 조건은 기본 검색 쿼리에 영향을 주지 않습니다. Beta에 참여하려면 [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com)에 전자 메일 요청을 보내십시오.

Live Search Beta를 설치하려면 [Live Search 안내서](https://experienceleague.adobe.com/en/docs/commerce/live-search/install#install-the-live-search-beta)를 참조하세요.

### IBM Sterling Order Management 시스템 통합(Private Beta)

이 IBM Sterling Order Management용 통합 가속기를 통해 Adobe Commerce 고객은 IBM Sterling OMS에서 제공하는 고급 주문 관리 기능을 시작할 수 있습니다. 이 통합을 통해 판매자는 다음과 같은 이점을 얻을 수 있습니다.

- 고객의 재고 수준과 정확한 납품 일자에 대한 실시간 가시성.
- 구성 가능한 규칙을 기반으로 한 주문의 자동 소싱을 통해 이행 네트워크 및 재고를 최적화할 수 있습니다.
- 지원 팀이 탁월한 서비스를 제공하고 예외를 신속하게 식별하고 처리할 수 있도록 단일 대시보드의 채널 전체에 대한 주문 보편적 보기.
- 반환 관리를 단순화하는 템플릿화된 반환 관리 플로우입니다.

이 Beta에 참여하려면 [sbieber@adobe.com](mailto:sbieber@adobe.com)(으)로 전자 메일 요청을 보내십시오.

### Adobe Commerce Foundation(공개 Alpha/Beta)

각 Adobe Commerce Foundation 알파 및 베타 릴리스에는 다음 기능 영역을 포함하되, 이에 국한되지 않는 예약된 릴리스 날짜까지 Adobe Commerce 핵심 코드에 전달되는 모든 변경 사항이 포함됩니다.

- 최신 보안 수정 사항
- 성능 향상
- GraphQL 개선 사항
- 일반 품질 버그 수정
- 커뮤니티 기여
- [Adobe Commerce 서비스](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)와의 호환성을 지원하는 데 필요한 변경 사항

#### 명명 규칙 및 일정

Adobe은 일반적으로 1년에 여러 번 알파 및 베타 패치를 출시합니다.

Alpha 릴리스 패키지에는 `-alphaX` 접미사가 있습니다. 예를 들어, Adobe Commerce 2.4.7 알파 릴리스 패키지는 다음 명명 규칙을 사용합니다.

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta 릴리스 패키지에는 `-betaX` 접미사가 있습니다. 예를 들어 Adobe Commerce 2.4.7 베타 릴리스 패키지는 다음 명명 규칙을 사용합니다.

- `2.4.7-beta1`
- `2.4.7-beta2`

예정된 공개 알파 및 베타 릴리스 날짜는 [릴리스 일정](schedule.md)을 참조하세요.

#### 액세스 해제

Adobe Commerce 알파 및 베타 릴리스는 다른 Adobe Commerce 패치 릴리스와 동일한 방식으로 배포됩니다. 이는 `https://repo.magento.com`의 Composer 메타패키지입니다. 소스 코드는 [GitHub](https://github.com/magento/magento2)에서 사용할 수 있습니다.

자세한 내용은 [작성기 설치 빠른 시작](../installation/composer.md)을 참조하십시오.

#### 문제 보고

Adobe은 알파 및 베타 릴리스에 대한 표준 Adobe 지원 서비스를 제공하지 않습니다.

알파 및 베타 릴리스와 관련된 피드백을 제출하려면 [GitHub](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)의 [일반 문제 보고 흐름](https://github.com/magento/magento2)을 따르십시오.

Adobe은 최신 알파 또는 베타 릴리스에 대해 보고된 모든 중요한 문제를 모니터링하고 GA 릴리스 날짜 이전에 해결되도록 우선 순위를 지정합니다.
