---
title: Adobe Commerce 2.4.6 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.6의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '1598'
ht-degree: 0%

---


# Adobe Commerce 2.4.6 보안 패치 릴리스 노트

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p13

Adobe Commerce 2.4.6-p13 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### 알려진 문제

#### 인벤토리 작성기 설치 관리자 패키지 누락

이 버전에는 이전 버전과 호환되지 않는 변경 내용이 있는 이전 부 버전에서 원활하게 업그레이드하는 데 필요한 `magento/inventory-composer-installer` 패키지가 포함되어 있지 않습니다.

2.3에서 2.4.6-p13으로 업그레이드하는 경우 업그레이드하기 전에 다음 명령을 실행하여 `magento/inventory-composer-installer` 패키지를 설치하십시오.

```bash
composer require magento/inventory-composer-installer
```

#### 체크아웃 페이지가 static.min.js 및 mixins.min.js를 로드하지 못했습니다.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.6-p12

Adobe Commerce 2.4.6-p12 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)을 참조하십시오.

{{b2b-patches}}

## 2.4.6-p11

Adobe Commerce 2.4.6-p11 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

* **MariaDB 지원**—MariaDB 10.11에 대한 지원이 추가되었습니다.

* **API 성능 향상**—이전 보안 패치 이후에 도입된 일괄 비동기 웹 API 끝점의 성능 저하를 해결합니다.<!-- AC-14078 -->

* **CMS 차단 액세스 수정**—머천다이징 전용 액세스와 같이 권한이 제한된 관리자가 [!UICONTROL CMS Blocks] 목록 페이지를 볼 수 없는 문제를 해결합니다.

  이전에는 이러한 사용자가 이전 보안 패치를 설치한 후 구성 매개 변수가 누락되어 오류가 발생했습니다.<!-- AC-14087 -->

* **쿠키 제한 호환성**—프레임워크에서 `MAX_NUM_COOKIES` 상수와 관련된 이전 버전과 호환되지 않는 변경 내용을 해결합니다. 이 업데이트는 예상되는 동작을 복원하고 쿠키 제한과 상호 작용하는 확장 또는 사용자 지정에 대한 호환성을 보장합니다.<!-- AC-14475 -->

* **비동기 작업**—이전 고객의 주문을 재정의하기 위한 제한된 비동기 작업입니다.<!-- AC-13917 -->

## 2.4.6-p10

Adobe Commerce 2.4.6-p10 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

Adobe Commerce 2.4.6-p9 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

Adobe Commerce 2.4.6-p8 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 이 릴리스에 포함된 핫픽스

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

Adobe Commerce 2.4.6-p7 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)을 참조하십시오.

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 이 릴리스에 포함된 핫픽스

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

Adobe Commerce 2.4.6-p6 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)을 참조하십시오.

Commerce 버전 2.4.6-p6과의 호환성을 위해 Adobe Commerce B2B 확장 기능이 있는 판매자는 [B2B 버전 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)&#x200B;(으)로 업그레이드해야 합니다.

### CVE-2024-34102용 핫픽스 적용

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Commerce 버전 2.4.6-p6과의 호환성을 위해 Adobe Commerce B2B 확장 기능이 있는 판매자는 [B2B 버전 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)&#x200B;(으)로 업그레이드해야 합니다.

### 강조 표시

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

Adobe Commerce 2.4.6-p5 보안 릴리스는 이전 릴리스 2.4.6에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

이러한 수정 사항에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)을 참조하십시오.

## 2.4.6-p4

Adobe Commerce 2.4.6-p4 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)을 참조하십시오.

### 강조 표시

이번 릴리스에는 다음과 같은 두 가지 중요한 보안 개선 사항이 도입되었습니다.

* **생성되지 않은 캐시 키의 동작을 변경합니다**:

   * 이제 블록에 대해 생성되지 않은 캐시 키에는 자동으로 생성되는 키의 접두사와 다른 접두사가 포함됩니다. (생성되지 않은 캐시 키는 템플릿 지시문 구문 또는 `setCacheKey` 또는 `setData` 메서드를 통해 설정된 키입니다.)
   * 이제 블록의 생성되지 않은 캐시 키에는 문자, 숫자, 하이픈(-) 및 밑줄(_)만 사용해야 합니다. <!-- AC-9831 -->

* **자동 생성된 쿠폰 코드 수에 대한 제한**. 이제 Commerce에서 자동으로 생성되는 쿠폰 코드 수를 제한합니다. 기본 최대값은 250,000입니다. 판매자는 새 **[!UICONTROL Code Quantity Limit]** 구성 옵션(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)을 사용하여 이 새 제한을 제어할 수 있습니다. <!-- AC-8753 -->

## 2.4.6-p3

Adobe Commerce 2.4.6-p3 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 준수하도록 개선된 보안 기능도 포함되어 있습니다.

보안 수정 사항에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)을 참조하십시오.

### 강조 표시

이 릴리스에서는 `{BASE-URL}/page_cache/block/esi HTTP` 끝점과 관련된 위험을 완화하는 데 도움이 되는 새로운 전체 페이지 캐시 구성 설정을 도입했습니다. 이 끝점은 Commerce 레이아웃 핸들과 블록 구조에서 제한되지 않고 동적으로 로드된 콘텐츠 조각을 지원합니다. 새 **[!UICONTROL Handles Param]** 구성 설정은 API당 허용되는 최대 핸들 수를 결정하는 이 끝점의 `handles` 매개 변수의 값을 설정합니다. 이 속성의 기본값은 100입니다. 판매자는 관리자(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)에서 이 값을 변경할 수 있습니다. <!-- AC-9113 -->

### 이 릴리스에 포함된 핫픽스

Adobe Commerce 2.4.6-p3에는 패치 ACSD-51892에 의해 해결된 성능 저하 해결책이 포함되어 있습니다. 판매자는 이 패치가 다루는 문제의 영향을 받지 않습니다. 이 문제는 [ACSD-51892: 구성 파일이 여러 번 로드되는 성능 문제](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) 기술 자료 문서에 설명되어 있습니다.

### 알려진 문제

**문제**: `wrong checksum`에서 작성기가 다운로드하는 동안 Adobe Commerce에 `repo.magento.com` 오류가 표시되고 패키지 다운로드가 중단됩니다. 이 문제는 프리릴리스 기간 동안 사용할 수 있는 릴리스 패키지를 다운로드하는 동안 발생할 수 있으며, 이는 `magento/module-page-cache` 패키지를 다시 패키징했기 때문입니다.

**해결 방법**: 다운로드하는 동안 이 오류가 표시되는 판매자는 다음 단계를 수행할 수 있습니다.

1) 프로젝트 내에 `/vendor` 디렉터리가 있으면 삭제합니다.
2) `bin/magento composer update magento/module-page-cache` 명령을 실행합니다. 이 명령은 `page cache` 패키지만 업데이트합니다.

체크섬 문제가 계속되면 `composer.lock` 명령을 다시 실행하여 모든 패키지를 업데이트하기 전에 `bin/magento composer update` 파일을 제거하십시오.

## 2.4.6-p2

Adobe Commerce 2.4.6-p2 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에서는 최신 보안 모범 사례를 통해 규정 준수를 개선할 수 있는 보안 개선 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)을 참조하십시오.

### CVE-2022-31160용 핫픽스 적용

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [jQuery UI 보안 취약점 CVE-2022-31160 수정 사항 for 2.4.4, 2.4.5 및 2.4.6 릴리스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서에 지정된 패치를 적용해야 합니다.

### 강조 표시

`fastcgi_pass` 파일의 `nginx.sample` 값이 `fastcgi_backend`의 이전(pre-2.4.6-p1) 값으로 반환되었습니다. 이 값은 Adobe Commerce 2.4.6-p1에서 실수로 `php-fpm:9000`(으)로 변경되었습니다.

### 이 릴리스에 포함된 핫픽스

Adobe Commerce 2.4.6-p2에는 패치 ACSD-51892에서 해결한 성능 저하 해결 방법이 포함되어 있습니다. 판매자는 이 패치가 다루는 문제의 영향을 받지 않습니다. 이 문제는 [ACSD-51892: 구성 파일이 여러 번 로드되는 성능 문제](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) 기술 자료 문서에 설명되어 있습니다.

## 2.4.6-p1

Adobe Commerce 2.4.6-p1 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 또한 이번 릴리스에는 최신 보안 모범 사례를 통해 규정 준수를 개선하기 위한 보안 개선 사항 및 플랫폼 업그레이드가 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html)을 참조하십시오.

### CVE-2022-31160용 핫픽스 적용

`jQuery-UI` 라이브러리 버전 1.13.1에는 여러 버전의 Adobe Commerce 및 Magento Open Source에 영향을 주는 알려진 보안 취약점(CVE-2022-31160)이 있습니다. 이 라이브러리는 Adobe Commerce 및 Magento Open Source 2.4.4, 2.4.5, 2.4.6의 종속성입니다. 영향을 받는 배포를 실행하는 판매자는 [쿼리 UI 보안 취약점 CVE-2022-31160 수정 사항(2.4.4, 2.4.5 및 2.4.6 릴리스)에 지정된 패치를 적용해야 합니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 기술 자료 문서.

#### 강조

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL 쿼리 및 ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST 끝점의 기본 동작이 변경되었습니다. 기본적으로 이제 API는 항상 `true`을(를) 반환합니다. 판매자는 데이터베이스에 전자 메일이 없는 경우 `true`을(를) 반환하고 있는 경우 `false`을(를) 반환하는 원래 동작을 사용할 수 있습니다. <!-- AC-6695 -->

### 플랫폼 업그레이드

이 릴리스에 대한 플랫폼 업그레이드는 최신 보안 모범 사례를 통해 규정 준수를 개선합니다.

* **Varnish 캐시 7.3 지원**. 이 릴리스는 최신 버전의 Varnish Cache 7.3과 호환됩니다. 6.0.x 및 7.2.x 버전과의 호환성은 유지되지만, Adobe에서는 Adobe Commerce 2.4.6-p1을 Varnish Cache 버전 7.3 또는 버전 6.0 LTS와만 사용하는 것이 좋습니다.

* **RabbitMQ 3.11 지원**. 이 릴리스는 RabbitMQ 3.11의 최신 버전과 호환됩니다. RabbitMQ 3.9와의 호환성은 2023년 8월까지 지원되지만, Adobe에서는 RabbitMQ 3.11에서만 Adobe Commerce 2.4.6-p1을 사용하는 것이 좋습니다.

* **JavaScript 라이브러리**. 오래된 JavaScript 라이브러리가 `moment.js` 라이브러리(v2.29.4), `jQuery UI` 라이브러리(v1.13.2) 및 `jQuery` 유효성 검사 플러그인 라이브러리(v1.19.5)를 비롯한 최신 부 또는 패치 버전으로 업그레이드되었습니다.

### 알려진 문제

* `nginx.sample` 파일이 실수로 `fastcgi_pass`의 값을 `fastcgi_backend`에서 `php-fpm:9000`(으)로 수정하는 변경 내용으로 업데이트되었습니다. 이 변경 사항은 안전하게 되돌리거나 무시할 수 있습니다. <!-- AC-8992 -->

* B2B 보안 패키지에 대한 종속성이 없으면 B2B 확장을 1.4.0으로 설치하거나 업그레이드할 때 다음 설치 오류가 발생합니다.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  [안정성 태그](https://getcomposer.org/doc/04-schema.md#package-links)가 있는 B2B 보안 패키지에 대한 수동 종속성을 추가하여 이 문제를 해결할 수 있습니다. 자세한 내용은 [B2B 릴리스 정보](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue)를 참조하세요.

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
