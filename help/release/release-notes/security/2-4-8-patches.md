---
title: Adobe Commerce 2.4.8 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.8의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a61409b02e612295fb03a42e22dcfdf5c3eb0e57
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# Adobe Commerce 2.4.8 보안 패치 릴리스 노트

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p5

Adobe Commerce 2.4.8-p5 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB26-49](https://helpx.adobe.com/kr/security/products/magento/apsb26-49.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

#### MariaDB 11.8 호환성

Adobe Commerce 2.4.8은 MariaDB 11.4에 대한 지원을 유지하면서 MariaDB 11.8과의 호환성을 검증받았습니다. 이 업데이트는 플랫폼 안정성을 유지하기 위해 MariaDB 11.8에 도입된 SQL 동작 변경, 기본 업데이트 및 사용 중단을 해결합니다.

#### OpenSearch 3 최신 부 버전 지원

이제 Adobe Commerce 2.4.8은 Adobe Commerce on cloud infrastructure, Cloud Native 및 온프레미스 배포의 최신 부 버전의 OpenSearch 3를 지원합니다. OpenSearch 2와의 호환성은 유지됩니다.

#### Valkey 9.x LTS 지원

Adobe Commerce 2.4.8은 이제 Valkey 9.x LTS와 호환되며, 클라우드 인프라의 Adobe Commerce에서 지원되는 장기 지원 캐시 백엔드 옵션을 제공합니다.

#### RabbitMQ 4.2 지원

Adobe Commerce 2.4.8은 이제 2026년 2월로 예정된 RabbitMQ 4.1 지원 종료 날짜를 해결하는 RabbitMQ 4.2와 호환됩니다. Apache ActiveMQ Artemis와의 호환성은 유지되고 ActiveMQ는 이 보안 전용 릴리스 라인의 기본 메시지 큐 서비스로 유지됩니다.

#### USPS REST API 지원

USPS 배송 통합은 이제 기존 Web Tools API 외에도 현대화된 RESTful USPS API를 지원합니다. 관리자는 관리 구성에서 사용할 USPS 통합 API를 선택할 수 있습니다. 이 업데이트는 USPS Web Tools API 사용 중단을 준비합니다.

#### Magento 소유 Laminas MVC 포크

Laminas MVC 사용 중단을 해결하기 위해 이제 Adobe Commerce에서 `laminas-mvc`(`magento/magento-zf-mvc`(으)로 게시됨)의 Magento 소유 포크를 사용합니다. 이 포크를 사용하면 Adobe Commerce 2.4.8에 대한 지속적인 패치뿐만 아니라 장기적인 보안 규정 준수도 보장됩니다.

## 2.4.8-p4

Adobe Commerce 2.4.8-p4 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB26-05](https://helpx.adobe.com/kr/security/products/magento/apsb26-05.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

#### DHL 배송 통합을 위한 MyDHL REST API 지원

이제 DHL 배송 통합은 기존 DHL Express XML 통합 외에도 MyDHL REST API를 지원합니다. 이 업데이트는 DHL의 현재 API 스택에 맞게 조정되며 이전 XML API의 사용을 중단할 준비를 합니다.

#### 최신 Composer 버전과의 호환성 추가

Adobe Commerce 2.4.8은 Composer 2.2 LTS와 호환되지만 Composer 2.9.x를 지원하도록 업데이트되었습니다.

## 2.4.8-p3

Adobe Commerce 2.4.8-p3 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-94](https://helpx.adobe.com/kr/security/products/magento/apsb25-94.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* ACP2E-3874에 대한 수정: 동일한 여러 항목을 주문한 경우 주문 세부 사항에 대한 REST API 응답에 `base_row_total` 및 `row_total` 특성에 대한 올바른 값이 포함되어 있습니다.

* AC-15446 수정: `getBodyText()`이(가) `Symfony\Component\Mime\Message`에서 존재하지 않는 `getTextBody()` 메서드를 호출하려고 시도하여 Magento 2.4.8-p2 및 `magento/framework` 103.0.8-p2와의 호환성을 보장하는 `Magento\Framework\Mail\EmailMessage`의 오류가 수정되었습니다.

{{oct-2025-backports}}

### 알려진 문제

#### 체크아웃 페이지가 static.min.js 및 mixins.min.js를 로드하지 못했습니다.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

Adobe Commerce 2.4.8-p2 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-71](https://helpx.adobe.com/kr/security/products/magento/apsb25-71.html)을 참조하십시오.

{{b2b-patches}}

## 2.4.8-p1

Adobe Commerce 2.4.8-p1 보안 릴리스는 이전 릴리스 2.4.8에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-50](https://helpx.adobe.com/kr/security/products/magento/apsb25-50.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

* **API 성능 향상**—이전 보안 패치 이후에 도입된 일괄 비동기 웹 API 끝점의 성능 저하를 해결합니다.<!-- AC-14078 -->

* **CMS 차단 액세스 수정**—머천다이징 전용 액세스와 같이 권한이 제한된 관리자가 [!UICONTROL CMS Blocks] 목록 페이지를 볼 수 없는 문제를 해결합니다.

  이전에는 이러한 사용자가 이전 보안 패치를 설치한 후 구성 매개 변수가 누락되어 오류가 발생했습니다.<!-- AC-14087 -->

* **쿠키 제한 호환성**—프레임워크에서 `MAX_NUM_COOKIES` 상수와 관련된 이전 버전과 호환되지 않는 변경 내용을 해결합니다. 이 업데이트는 예상되는 동작을 복원하고 쿠키 제한과 상호 작용하는 확장 또는 사용자 지정에 대한 호환성을 보장합니다.<!-- AC-14475 -->

* **비동기 작업**—이전 고객의 주문을 재정의하기 위한 제한된 비동기 작업입니다.<!-- AC-13917 -->

* **CVE-2025-47110에 대한 수정**—전자 메일 템플릿 취약점을 해결합니다.<!-- AC-14695 -->

* **VULN-31547에 대한 수정**—범주 표준 링크 취약성을 해결합니다.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110 및 VULN-31547에 대한 수정 사항은 격리된 패치로도 사용할 수 있습니다. 자세한 내용은 [기술 자료 문서](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)를 참조하세요.

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-04-08 15:01:38 -->
