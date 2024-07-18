---
title: Adobe Commerce 2.4.5 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.5의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 2269c99908c0f8292ad62bd5837b1b8cebd50cb3
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 0%

---


# Adobe Commerce 2.4.5 보안 패치 릴리스 노트

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

Adobe Commerce 2.4.5-p7 보안 릴리스는 이전 릴리스 2.4.5에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)을 참조하십시오.

### CVE-2024-34102용 핫픽스 적용

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### 플랫폼 업그레이드

* **MariaDB 10.5 지원**. 이 패치 릴리스는 MariaDB 버전 10.5와의 호환성을 제공합니다. Adobe CommerceAdobe 는 여전히 MariaDB 버전 10.4와 호환되지만, MariaDB 10.4 유지 보수는 2024년 6월 18일에 종료되므로 Adobe Commerce 2.4.5-p8 및 예정된 모든 2.4.5 보안 전용 패치 릴리스를 MariaDB 버전 10.5와만 사용하는 것이 좋습니다. <!--AC-11530-->

### 추가적인 보안 개선 사항

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

Adobe Commerce 2.4.5-p7 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)을 참조하십시오.

## Adobe Commerce 2.4.5-p6

Adobe Commerce 2.4.5-p6 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 준수하도록 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)을 참조하십시오.

### 보안 주요 사항

이번 릴리스에는 다음과 같은 두 가지 중요한 보안 개선 사항이 도입되었습니다.

* **생성되지 않은 캐시 키의 동작을 변경합니다**:

   * 이제 블록에 대해 생성되지 않은 캐시 키에는 자동으로 생성되는 키의 접두사와 다른 접두사가 포함됩니다. (생성되지 않은 캐시 키는 템플릿 지시문 구문 또는 `setCacheKey` 또는 `setData` 메서드를 통해 설정된 키입니다.)
   * 이제 블록의 생성되지 않은 캐시 키에는 문자, 숫자, 하이픈(-) 및 밑줄(_)만 사용해야 합니다. <!-- AC-9831 -->

* **자동 생성된 쿠폰 코드 수에 대한 제한**. 이제 Commerce에서 자동으로 생성되는 쿠폰 코드 수를 제한합니다. 기본 최대값은 250,000입니다. 판매자는 새 **[!UICONTROL Code Quantity Limit]** 구성 옵션(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)을 사용하여 이 새 제한을 제어할 수 있습니다. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Adobe Commerce 2.4.5-p5 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 준수하도록 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)을 참조하십시오.

### 보안 강조 표시

이 릴리스에서는 `{BASE-URL}/page_cache/block/esi HTTP` 끝점과 관련된 위험을 완화하는 데 도움이 되는 새로운 전체 페이지 캐시 구성 설정을 도입했습니다. 이 끝점은 Commerce 레이아웃 핸들과 블록 구조에서 제한되지 않고 동적으로 로드된 콘텐츠 조각을 지원합니다. 새 **[!UICONTROL Handles Param]** 구성 설정은 API당 허용되는 최대 핸들 수를 결정하는 이 끝점의 `handles` 매개 변수의 값을 설정합니다. 이 속성의 기본값은 100입니다. 판매자는 관리자(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)에서 이 값을 변경할 수 있습니다. <!-- AC-9113 -->

### 알려진 문제

**문제**: `repo.magento.com`에서 작성기가 다운로드하는 동안 Adobe Commerce에 **잘못된 체크섬** 오류가 표시되고 패키지 다운로드가 중단됩니다. 이 문제는 프리릴리스 중에 제공된 릴리스 패키지를 다운로드하는 동안 발생할 수 있으며 이는 `magento/module-page-cache` 패키지를 다시 패키징했기 때문입니다.

**해결 방법**: 다운로드하는 동안 이 오류가 표시되는 판매자는 다음 단계를 수행할 수 있습니다.

1) 프로젝트 내에 `/vendor` 디렉터리가 있으면 삭제합니다.
2) `bin/magento composer update magento/module-page-cache` 명령을 실행합니다. 이 명령은 `page cache` 패키지만 업데이트합니다.

체크섬 문제가 계속되면 `bin/magento composer update` 명령을 다시 실행하여 모든 패키지를 업데이트하기 전에 `composer.lock` 파일을 제거하십시오.

## Adobe Commerce 2.4.5-p4

Adobe Commerce 2.4.5-p4 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)을 참조하십시오.

### jQuery-UI 라이브러리에서 패치를 적용하여 보안 취약성 해결 CVE-2022-31160

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [jQuery UI 보안 취약점 CVE-2022-31160 수정 사항 for 2.4.4, 2.4.5 및 2.4.6 릴리스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서에 지정된 패치를 적용해야 합니다.

## Adobe Commerce 2.4.5-p3

Adobe Commerce 2.4.5-p3 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [보안 게시판 Adobe](https://helpx.adobe.com/security/products/magento/apsb23-35.html)을 참조하십시오.

### jQuery-UI 라이브러리에서 패치를 적용하여 보안 취약성 해결 CVE-2022-31160

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [쿼리 UI 보안 취약점 CVE-2022-31160 수정 사항(2.4.4, 2.4.5 및 2.4.6 릴리스)에 지정된 패치를 적용해야 합니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서.

### 보안 강조 표시

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL 쿼리 및 ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST 끝점의 기본 동작이 변경되었습니다. 기본적으로 이제 API는 항상 `true`을(를) 반환합니다. 판매자는 데이터베이스에 전자 메일이 없는 경우 `true`을(를) 반환하고 있는 경우 `false`을(를) 반환하는 원래 동작을 사용할 수 있습니다. <!-- AC-6695 -->

### 플랫폼 업그레이드

이 릴리스에 대한 플랫폼 업그레이드는 최신 보안 모범 사례를 통해 규정 준수를 개선합니다.

* **Varnish 캐시 7.3 지원**. 이 릴리스는 최신 버전의 Varnish Cache 7.3과 호환됩니다. 6.0.x 및 7.2.x 버전과의 호환성은 유지되지만, Adobe Commerce 2.4.5-p3를 Varnish Cache 버전 7.3 또는 버전 6.0 LTS와만 사용하는 것이 좋습니다.

* **RabbitMQ 3.11 지원**. 이 릴리스는 RabbitMQ 3.11의 최신 버전과 호환됩니다. RabbitMQ 3.9와의 호환성은 2023년 8월까지 지원되지만, RabbitMQ 3.11에서만 Adobe Commerce 2.4.5-p3을 사용하는 것이 좋습니다.

* **JavaScript 라이브러리**. 오래된 JavaScript 라이브러리가 `moment.js` 라이브러리(v2.29.4), `jQuery UI` 라이브러리(v1.13.2) 및 `jQuery` 유효성 검사 플러그인 라이브러리(v1.19.5)를 비롯한 최신 부 또는 패치 버전으로 업그레이드되었습니다.

## Adobe Commerce 2.4.5-p2 릴리스 노트

Adobe Commerce 2.4.5-p2 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 세 가지 보안 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html)을 참조하십시오.

## Adobe Commerce 2.4.5-p1

Adobe Commerce 2.4.5-p1 보안 릴리스는 이전 릴리스(Adobe Commerce 2.4.5 및 Magento Open Source 2.4.5)에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html)을 참조하십시오.

보안 버그 수정 중 하나에 새 구성 설정 생성이 포함되었습니다. **전자 메일이 변경된 경우 전자 메일 확인 필요** 구성 설정을 사용하면 관리자가 전자 메일 주소를 변경할 때 전자 메일 확인을 요구할 수 있습니다. <!-- AC-6292-->
