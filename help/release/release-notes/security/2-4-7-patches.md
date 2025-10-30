---
title: Adobe Commerce 2.4.7 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.7의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 5f0914e92e5d1f1a27640a12a36c73ce878687a0
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Adobe Commerce 2.4.7 보안 패치 릴리스 노트

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p8

Adobe Commerce 2.4.7-p8 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)을 참조하십시오.

{{b2b-patches}}

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### 알려진 문제

#### 체크아웃 페이지가 static.min.js 및 mixins.min.js를 로드하지 못했습니다.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.7-p7

Adobe Commerce 2.4.7-p7 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)을 참조하십시오.

{{b2b-patches}}

## 2.4.7-p6

Adobe Commerce 2.4.7-p6 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

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

## 2.4.7-p5

Adobe Commerce 2.4.7-p5 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

이 릴리스에서는 Adobe Commerce [HIPAA 지원 확장](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)에 대한 지원도 도입되었습니다.

>[!ENDSHADEBOX]

### 알려진 문제

**문제**: PHP 8.2 이상이 있는 2.4.7-p5를 설치할 때, 시스템은 2.4.8 이상을 위한 `paypal/module-braintree` 버전 4.7.0을 설치합니다. PHP 8.1의 경우 올바른 Braintree 버전 4.6.1-p5가 사용됩니다. 이 불일치는 메타패키지의 `adobe-commerce/extensions-metapackage: ~2.0`에 대한 느슨한 종속성 때문입니다. PHP 8.2 이상 배포에 대한 호환성 및 지원되는 기능 집합에 영향을 줍니다.<!-- ACPLTSRV-6276) -->

또한 버전 2.4.7-p3, 2.4.7-p4 및 2.4.7-p5의 경우 Braintree 확장 버전 4.6.1-p5를 설치할 수 있지만 일부 사용자는 릴리스 라인 내에서 확장 업그레이드를 허용하도록 완화된 이전 보다 엄격한 종속성으로 인해 4.6.1-p3 또는 p4를 예상할 수 있습니다. <!-- AC-14430 -->

**해결 방법**: PHP 버전에 대한 올바른 Braintree 버전이 있는지 확인하려면 `composer update`을(를) 실행하여 `adobe-commerce/extensions-metapackage:2.0.0` 종속성에 따라 적절한 버전을 설치하십시오.

## 2.4.7-p4

Adobe Commerce 2.4.7-p4 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

Adobe Commerce 2.4.7-p3 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)을 참조하십시오.

{{b2b-patches}}

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 이 릴리스에 포함된 핫픽스

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

Adobe Commerce 2.4.7-p2 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)을 참조하십시오.

### 강조 표시

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 이 릴리스에 포함된 핫픽스

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

Adobe Commerce 2.4.7-p1 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)을 참조하십시오.

### CVE-2024-34102용 핫픽스 적용

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 강조 표시

이번 릴리스에는 다음과 같은 주요 사항이 포함됩니다.

* **Google Authenticator에 대한 [OTP(일회성 암호) 설정](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)을 업데이트합니다**-이 업데이트는 2.4.7에서 [이전 버전과 호환되지 않는 변경](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)으로 인해 발생한 오류를 해결하는 데 필요합니다. 이제 **[!UICONTROL OTP Window]** 필드에 대한 설명에 설정에 대한 정확한 설명이 있으며 기본값이 `1`에서 `29`(으)로 변경되었습니다.

* **B2B 버전 호환성** - Commerce 버전 2.4.7-p1과의 호환성을 위해 Adobe Commerce B2B 확장 기능이 있는 판매자는 [B2B 버전 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)&#x200B;(으)로 업그레이드해야 합니다.

### 이 릴리스에 포함된 핫픽스

Adobe Commerce 2.4.7-p1은 SOAP에서 REST API로 UPS 통합 마이그레이션 범위에서 도입된 문제를 해결합니다. 이 문제는 미국 외에서 배송하는 고객에게 영향을 미쳐 UPS로 배송을 생성하는 포장물에 킬로그램 및 센티미터의 지표 시스템/SI 측정을 사용할 수 없게 했습니다. 자세한 내용은 [SOAP에서 RESTful API로 UPS 배송 방법 통합 마이그레이션](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) 기술 자료 문서를 참조하십시오.

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
