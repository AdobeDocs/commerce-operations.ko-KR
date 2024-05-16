---
title: Adobe Commerce 2.4.5 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.5의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---


# Adobe Commerce 2.4.5 보안 패치 릴리스 노트

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p7

Adobe Commerce 2.4.5-p7 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 게시판 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

Adobe Commerce 2.4.5-p6 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 준수하도록 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 게시판 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### 보안 주요 사항

이번 릴리스에는 다음과 같은 두 가지 중요한 보안 개선 사항이 도입되었습니다.

* **생성되지 않은 캐시 키 동작 변경**:

   * 이제 블록에 대해 생성되지 않은 캐시 키에는 자동으로 생성되는 키의 접두사와 다른 접두사가 포함됩니다. (생성되지 않은 캐시 키는 템플릿 지시문 구문 또는 `setCacheKey` 또는 `setData` 메서드.)
   * 이제 블록의 생성되지 않은 캐시 키에는 문자, 숫자, 하이픈(-) 및 밑줄(_)만 사용해야 합니다.  <!-- AC-9831 -->

* **자동 생성된 쿠폰 코드 수 제한**. 이제 Commerce에서 자동으로 생성되는 쿠폰 코드 수를 제한합니다. 기본 최대값은 250,000입니다. 상인은 새 제품을 사용할 수 있습니다 **[!UICONTROL Code Quantity Limit]** 구성 옵션 (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)을 클릭하여 이 새 제한을 제어합니다. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Adobe Commerce 2.4.5-p5 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 준수하도록 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 게시판 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### 보안 강조 표시

이 릴리스에는 와 관련된 위험을 완화하는 데 도움이 되는 새로운 전체 페이지 캐시 구성 설정이 도입되었습니다. `{BASE-URL}/page_cache/block/esi HTTP` 엔드포인트. 이 끝점은 상거래 레이아웃 핸들 및 블록 구조에서 제한되지 않고 동적으로 로드된 콘텐츠 조각을 지원합니다. 새로운 **[!UICONTROL Handles Param]** 구성 설정은 이 끝점의 값을 설정합니다. `handles` API당 허용되는 최대 핸들 수를 결정하는 매개 변수입니다. 이 속성의 기본값은 100입니다. 판매자는 관리자( )에서 이 값을 변경할 수 있습니다.**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### 알려진 문제

**문제**: Adobe Commerce에 **체크섬 오류** 에서 작성기로 다운로드하는 중 오류 발생 `repo.magento.com`, 및 패키지 다운로드가 중단되었습니다. 이 문제는 프리릴리스 중에 제공된 릴리스 패키지를 다운로드하는 동안 발생할 수 있으며 이 문제는 를 다시 패키징하여 발생합니다. `magento/module-page-cache` 패키지.

**해결 방법**: 다운로드 중에 이 오류가 표시되는 판매자는 다음 단계를 수행할 수 있습니다.

1) 삭제 `/vendor` 디렉터리가 있는 경우 프로젝트 내에 디렉터리가 있습니다.
2) 실행 `bin/magento composer update magento/module-page-cache` 명령입니다. 이 명령은 `page cache` 패키지.

체크섬 문제가 지속되면 `composer.lock` 파일을 다시 실행하기 전에 `bin/magento composer update` 모든 패키지를 업데이트하는 명령입니다.

## Adobe Commerce 2.4.5-p4

Adobe Commerce 2.4.5-p4 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 게시판 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### jQuery-UI 라이브러리에서 패치를 적용하여 보안 취약성 해결 CVE-2022-31160

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [jQuery UI 보안 취약성 CVE-2022-31160 2.4.4, 2.4.5 및 2.4.6 릴리스에 대한 수정 사항](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서입니다.

## Adobe Commerce 2.4.5-p3

Adobe Commerce 2.4.5-p3 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 공지](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### jQuery-UI 라이브러리에서 패치를 적용하여 보안 취약성 해결 CVE-2022-31160

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [2.4.4, 2.4.5 및 2.4.6 릴리스에 대한 쿼리 UI 보안 취약성 CVE-2022-31160 수정](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서입니다.

### 보안 강조 표시

의 기본 동작 [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL 쿼리 및 ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST 끝점이 변경되었습니다. 기본적으로 이제 API는 항상 를 반환합니다 `true`. 판매자는 원래의 비헤이비어 즉, 반환을 활성화할 수 있습니다 `true` 데이터베이스에 이메일이 없는 경우 `false` 존재하는 경우. <!-- AC-6695 -->

### 플랫폼 업그레이드

이 릴리스에 대한 플랫폼 업그레이드는 최신 보안 모범 사례를 통해 규정 준수를 개선합니다.

* **Vannish cache 7.3 지원**. 이 릴리스는 최신 버전의 Varnish Cache 7.3과 호환됩니다. 6.0.x 및 7.2.x 버전과의 호환성은 유지되지만, Adobe Commerce 2.4.5-p3를 Varnish Cache 버전 7.3 또는 버전 6.0 LTS와만 사용하는 것이 좋습니다.

* **RabbitMQ 3.11 지원**. 이 릴리스는 RabbitMQ 3.11의 최신 버전과 호환됩니다. RabbitMQ 3.9와의 호환성은 2023년 8월까지 지원되지만, RabbitMQ 3.11에서만 Adobe Commerce 2.4.5-p3을 사용하는 것이 좋습니다.

* **JavaScript 라이브러리**. 오래된 JavaScript 라이브러리가 다음을 포함한 최신 부 또는 패치 버전으로 업그레이드되었습니다. `moment.js` 라이브러리(v2.29.4), `jQuery UI` 라이브러리(v1.13.2) 및 `jQuery` 유효성 검사 플러그인 라이브러리(v1.19.5).

## Adobe Commerce 2.4.5-p2 릴리스 노트

Adobe Commerce 2.4.5-p2 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 세 가지 보안 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 게시판 APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

Adobe Commerce 2.4.5-p1 보안 릴리스는 이전 릴리스(Adobe Commerce 2.4.5 및 Magento Open Source 2.4.5)에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 게시판 APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

보안 버그 수정 중 하나에 새 구성 설정 생성이 포함되었습니다. 다음 **이메일이 변경된 경우 이메일 확인 필요** 구성 설정을 사용하면 관리자가 전자 메일 주소를 변경할 때 전자 메일 확인이 필요합니다. <!-- AC-6292-->


