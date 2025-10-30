---
title: Adobe Commerce 2.4.4 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.4의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 5f0914e92e5d1f1a27640a12a36c73ce878687a0
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---


# Adobe Commerce 2.4.4 보안 패치 릴리스 노트

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.4-p16

Adobe Commerce 2.4.4-p16은 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정을 제공하는 확장 지원 보안 릴리스입니다. Adobe Commerce 고객만 사용할 수 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>2.4.4용 확장 지원 보안 패치는 Adobe Commerce 고객만 사용할 수 있습니다. 이러한 패치는 Magento Open Source 코드 기반에 사용할 수 없습니다. [확장 지원](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)을 참조하세요.

### 알려진 문제

#### 체크아웃 페이지가 static.min.js 및 mixins.min.js를 로드하지 못했습니다.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.4-p15

Adobe Commerce 2.4.4-p15는 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정을 제공하는 확장 지원 보안 릴리스입니다. Adobe Commerce 고객만 사용할 수 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)을 참조하십시오.

{{b2b-patches}}

## 2.4.4-p14

Adobe Commerce 2.4.4-p14는 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정을 제공하는 확장 지원 보안 릴리스입니다. Adobe Commerce 고객만 사용할 수 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

* **API 성능 향상**—이전 보안 패치 이후에 도입된 일괄 비동기 웹 API 끝점의 성능 저하를 해결합니다.<!-- AC-14078 -->

* **CMS 차단 액세스 수정**—머천다이징 전용 액세스와 같이 권한이 제한된 관리자가 [!UICONTROL CMS Blocks] 목록 페이지를 볼 수 없는 문제를 해결합니다.

  이전에는 이러한 사용자가 이전 보안 패치를 설치한 후 구성 매개 변수가 누락되어 오류가 발생했습니다.<!-- AC-14087 -->

* **쿠키 제한 호환성**—프레임워크에서 `MAX_NUM_COOKIES` 상수와 관련된 이전 버전과 호환되지 않는 변경 내용을 해결합니다. 이 업데이트는 예상되는 동작을 복원하고 쿠키 제한과 상호 작용하는 확장 또는 사용자 지정에 대한 호환성을 보장합니다.<!-- AC-14475 -->

* **비동기 작업**—이전 고객의 주문을 재정의하기 위한 제한된 비동기 작업입니다.<!-- AC-13917 -->

## 2.4.4-p13

Adobe Commerce 2.4.4-p13 보안 릴리스는 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.4-p12

Adobe Commerce 2.4.4-p12 보안 릴리스는 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

Adobe Commerce 2.4.4-p11 보안 릴리스는 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

Adobe Commerce 2.4.4-p10 보안 릴리스는 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)을 참조하십시오.

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 이 릴리스에 포함된 핫픽스

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

Adobe Commerce 2.4.4-p9 보안 릴리스는 이전 릴리스 2.4.4에서 식별된 취약점에 대한 보안 버그 수정을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)을 참조하십시오.

### CVE-2024-34102용 핫픽스 적용

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 플랫폼 업그레이드

* **MariaDB 10.5 지원**. 이 패치 릴리스는 MariaDB 버전 10.5와의 호환성을 제공합니다. Adobe Commerce은 여전히 MariaDB 버전 10.4와 호환되지만, MariaDB 10.4 유지 보수는 2024년 6월 18일에 종료되므로 Adobe에서는 Adobe Commerce 2.4.4-p9 및 예정된 모든 2.4.4 보안 전용 패치 릴리스를 MariaDB 버전 10.5와만 사용할 것을 권장합니다. <!--AC-11530-->

### 강조 표시

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

Adobe Commerce 2.4.4-p8 보안 릴리스는 Adobe Commerce 2.4.4 배포에 대한 보안 버그 수정 사항을 제공합니다. 이러한 업데이트는 이전 릴리스에서 식별된 취약점을 수정합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)을 참조하십시오.

## 2.4.4-p7

Adobe Commerce 2.4.4-p7 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)을 참조하십시오.

### 강조 표시

이번 릴리스에는 다음과 같은 두 가지 중요한 보안 개선 사항이 도입되었습니다.

* **생성되지 않은 캐시 키의 동작을 변경합니다**:

   * 이제 블록에 대해 생성되지 않은 캐시 키에는 자동으로 생성되는 키의 접두사와 다른 접두사가 포함됩니다. (생성되지 않은 캐시 키는 템플릿 지시문 구문 또는 `setCacheKey` 또는 `setData` 메서드를 통해 설정된 키입니다.)
   * 이제 블록의 생성되지 않은 캐시 키에는 문자, 숫자, 하이픈(-) 및 밑줄(_)만 사용해야 합니다. <!-- AC-9831 -->

* **자동 생성된 쿠폰 코드 수에 대한 제한**. 이제 Commerce에서 자동으로 생성되는 쿠폰 코드 수를 제한합니다. 기본 최대값은 250,000입니다. 판매자는 새 **[!UICONTROL Code Quantity Limit]** 구성 옵션(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)을 사용하여 이 새 제한을 제어할 수 있습니다. <!-- AC-8753 -->

## 2.4.4-p6

Adobe Commerce 2.4.4-p6 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)을 참조하십시오.

이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

### 강조 표시

이 릴리스에서는 `{BASE-URL}/page_cache/block/esi HTTP` 끝점과 관련된 위험을 완화하는 데 도움이 되는 새로운 전체 페이지 캐시 구성 설정을 도입했습니다. 이 끝점은 Commerce 레이아웃 핸들과 블록 구조에서 제한되지 않고 동적으로 로드된 콘텐츠 조각을 지원합니다. 새 **[!UICONTROL Handles Param]** 구성 설정은 API당 허용되는 최대 핸들 수를 결정하는 이 끝점의 `handles` 매개 변수의 값을 설정합니다. 이 속성의 기본값은 100입니다. 판매자는 관리자(**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)에서 이 값을 변경할 수 있습니다. <!-- AC-9113 -->

### 알려진 문제

**문제**: **에서 작성기가 다운로드하는 동안 Adobe Commerce에**&#x200B;잘못된 체크섬`repo.magento.com` 오류가 표시되고 패키지 다운로드가 중단됩니다. 이 문제는 프리릴리스 중에 제공된 릴리스 패키지를 다운로드하는 동안 발생할 수 있으며 이는 `magento/module-page-cache` 패키지를 다시 패키징했기 때문입니다.

**해결 방법**: 다운로드하는 동안 이 오류가 표시되는 판매자는 다음 단계를 수행할 수 있습니다.

1) 프로젝트 내에 `/vendor` 디렉터리가 있으면 삭제합니다.
2) `bin/magento composer update magento/module-page-cache` 명령을 실행합니다. 이 명령은 `page cache` 패키지만 업데이트합니다.

체크섬 문제가 계속되면 `composer.lock` 명령을 다시 실행하여 모든 패키지를 업데이트하기 전에 `bin/magento composer update` 파일을 제거하십시오.

## 2.4.4-p5

Adobe Commerce 2.4.4-p5 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)을 참조하십시오.

### CVE-2022-31160용 핫픽스 적용

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [jQuery UI 보안 취약점 CVE-2022-31160 수정 사항 for 2.4.4, 2.4.5 및 2.4.6 릴리스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서에 지정된 패치를 적용해야 합니다.

## 2.4.4-p4

Adobe Commerce 2.4.4-p4 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 통해 규정 준수를 개선하기 위한 보안 개선 사항 및 플랫폼 업그레이드가 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html)을 참조하십시오.

### CVE-2022-31160용 핫픽스 적용

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [jQuery UI 보안 취약점 CVE-2022-31160 수정 사항 for 2.4.4, 2.4.5 및 2.4.6 릴리스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서에 지정된 패치를 적용해야 합니다.

### 강조 표시

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL 쿼리 및 ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST 끝점의 기본 동작이 변경되었습니다. 기본적으로 이제 API는 항상 `true`을(를) 반환합니다. 판매자는 데이터베이스에 전자 메일이 없는 경우 `true`을(를) 반환하고 있는 경우 `false`을(를) 반환하는 원래 동작을 사용할 수 있습니다. <!-- AC-6695 -->

### 플랫폼 업그레이드

이 릴리스에 대한 플랫폼 업그레이드는 최신 보안 모범 사례를 통해 규정 준수를 개선합니다.

* **Varnish 캐시 7.3 지원**. 이 릴리스는 최신 버전의 Varnish Cache 7.3과 호환됩니다. 6.0.x 및 7u.2.x 버전과의 호환성은 유지되지만, Adobe에서는 Adobe Commerce 2.4.4-p4를 Varnish Cache 버전 7.3 또는 버전 6.0 LTS와만 사용하는 것이 좋습니다.

* **RabbitMQ 3.11 지원**. 이 릴리스는 RabbitMQ 3.11의 최신 버전과 호환됩니다. RabbitMQ 3.9와의 호환성은 2023년 8월까지 지원되지만, Adobe에서는 RabbitMQ 3.11에서만 Adobe Commerce 2.4.4-p4를 사용하는 것이 좋습니다.

* **JavaScript 라이브러리**. 오래된 JavaScript 라이브러리가 `moment.js` 라이브러리(v2.29.4), `jQuery UI` 라이브러리(v1.13.2) 및 `jQuery` 유효성 검사 플러그인 라이브러리(v1.19.5)를 비롯한 최신 부 또는 패치 버전으로 업그레이드되었습니다.

## 2.4.4-p3

Adobe Commerce 2.4.4-p3 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html)을 참조하십시오.

## 2.4.4-p2

Adobe Commerce 2.4.4-p2 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 수정 사항을 제공합니다. 한 가지 수정 사항에는 새 구성 설정 생성이 포함됩니다. [!UICONTROL **전자 메일이 변경된 경우 전자 메일 확인 필요**] 구성 설정을 사용하면 관리자가 전자 메일 주소를 변경할 때 전자 메일 확인을 요구할 수 있습니다. <!-- AC-6292-->

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html)을 참조하십시오.

### AC-3022.patch를 적용하여 DHL을 배송 운송업체로 계속 제공

DHL은 스키마 버전 6.2를 도입했으며 조만간 스키마 버전 6.0을 더 이상 사용하지 않을 예정입니다. DHL 통합을 지원하는 Adobe Commerce 2.4.4 및 이전 버전은 버전 6.0만 지원합니다. 이러한 릴리스를 배포하는 판매자는 가능한 한 빨리 `AC-3022.patch`을(를) 적용하여 DHL을 운송 회사로 계속 제공해야 합니다. 패치 다운로드 및 설치에 대한 자세한 내용은 [DHL을 계속 제공하려면 패치 적용](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) 기술 자료 문서를 참조하십시오.

## 2.4.4-p1

Adobe Commerce 2.4.4-p1 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 준수하도록 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판](https://helpx.adobe.com/security/products/magento/apsb22-38.html)을 참조하십시오.t

### AC-3022.patch를 적용하여 DHL을 배송 운송업체로 계속 제공

DHL은 스키마 버전 6.2를 도입했으며 조만간 스키마 버전 6.0을 더 이상 사용하지 않을 예정입니다. DHL 통합을 지원하는 Adobe Commerce 2.4.4 및 이전 버전은 버전 6.0만 지원합니다. 이러한 릴리스를 배포하는 판매자는 가능한 한 빨리 `AC-3022.patch`을(를) 적용하여 DHL을 운송 회사로 계속 제공해야 합니다. 패치 다운로드 및 설치에 대한 자세한 내용은 [DHL을 계속 제공하려면 패치 적용](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) 기술 자료 문서를 참조하십시오.

### 강조 표시

이 릴리스의 보안 개선 사항은 다음을 포함하여 최신 보안 모범 사례를 준수하도록 개선합니다.

* ACL 리소스가 인벤토리에 추가되었습니다.
* 인벤토리 템플릿 보안이 향상되었습니다.

### 알려진 문제

**문제**: 2.4.4-p1 패키지에서 실행할 때 웹 API 및 통합 테스트에 이 오류가 표시됩니다. `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **해결 방법**: `require monolog/monolog:2.6.0` 명령을 실행하여 이전 버전의 Monolog를 설치하십시오. <!-- AC-3651-->

**문제**: 판매자는 Adobe Commerce 2.4.4에서 Adobe Commerce 2.4.4-p1로 업그레이드하는 동안 패키지 버전 다운그레이드 알림을 볼 수 있습니다. 이러한 메시지는 무시할 수 있습니다. 패키지 버전의 불일치는 패키지 생성 중 예외 항목에서 발생합니다. 제품 기능은 영향을 받지 않았습니다. 영향을 받는 시나리오 및 해결 방법에 대한 자세한 내용은 2.4.4에서 2.4.4-p1[ 기술 자료 문서로 업그레이드한 후 다운그레이드된 ](https://support.magento.com/hc/en-us/articles/8214752983949)패키지를 참조하십시오.

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
