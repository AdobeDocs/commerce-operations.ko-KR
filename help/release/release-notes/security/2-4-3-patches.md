---
title: Adobe Commerce 2.4.3 보안 패치 릴리스 정보
description: Adobe Commerce 버전 2.4.3의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---


# Adobe Commerce 2.4.3 보안 패치 릴리스 노트

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

Adobe Commerce 2.4.3-p3 보안 릴리스는 이전 릴리스 2.4.3에서 식별된 취약점에 대한 보안 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html)을 참조하십시오.

### AC-3022.patch를 적용하여 DHL을 배송 운송업체로 계속 제공

DHL은 스키마 버전 6.2를 도입했으며 조만간 스키마 버전 6.0을 더 이상 사용하지 않을 예정입니다. DHL 통합을 지원하는 Adobe Commerce 2.4.4 및 이전 버전은 버전 6.0만 지원합니다. 이러한 릴리스를 배포하는 판매자는 가능한 한 빨리 `AC-3022.patch`을(를) 적용하여 DHL을 운송 회사로 계속 제공해야 합니다. 패치 다운로드 및 설치에 대한 자세한 내용은 [DHL을 계속 제공하려면 패치 적용](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) 기술 자료 문서를 참조하십시오.

### 보안 주요 사항

* ACL 리소스가 인벤토리에 추가되었습니다.
* 인벤토리 템플릿 보안이 향상되었습니다.



## Adobe Commerce 2.4.3-p2

Adobe Commerce 2.4.3-p2 보안 릴리스는 이전 릴리스에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html)을 참조하십시오.  패치 릴리스는 `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`,`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` 및 `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`에서 해결된 취약성도 해결합니다.


### AC-3022.patch를 적용하여 DHL을 배송 운송업체로 계속 제공

DHL은 스키마 버전 6.2를 도입했으며 조만간 스키마 버전 6.0을 더 이상 사용하지 않을 예정입니다. DHL 통합을 지원하는 Adobe Commerce 2.4.4 및 이전 버전은 버전 6.0만 지원합니다. 이러한 릴리스를 배포하는 판매자는 가능한 한 빨리 `AC-3022.patch`을(를) 적용하여 DHL을 운송 회사로 계속 제공해야 합니다. 패치 다운로드 및 설치에 대한 자세한 내용은 [DHL을 계속 제공하려면 패치 적용](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) 기술 자료 문서를 참조하십시오.

### 보안 주요 사항

* 이메일 변수 사용은 보다 엄격한 변수 구문을 위해 보안 위험 완화의 일부로 2.3.4에서 더 이상 사용되지 않습니다. 이러한 기존 동작은 이러한 보안 위험 완화의 결과로 이번 릴리스에서 완전히 제거되었습니다.

  따라서 Adobe Commerce 2.4.3-p2로 업그레이드한 후 이전 버전에서 작동했던 이메일 또는 뉴스레터 템플릿이 제대로 작동하지 않을 수 있습니다. 영향을 받는 템플릿에는 관리자 무시, 테마, 하위 테마, 사용자 지정 모듈 또는 타사 확장의 템플릿이 포함됩니다. [호환성 업그레이드 도구](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html)를 사용하여 더 이상 사용되지 않는 사용을 해결한 후에도 배포에 영향을 줄 수 있습니다. 영향을 받는 템플릿 마이그레이션에 대한 잠재적 영향 및 지침에 대한 자세한 내용은 [사용자 지정 전자 메일 템플릿 마이그레이션](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/)을 참조하십시오.

* 이제 OAuth 액세스 토큰 및 암호 재설정 토큰은 데이터베이스에 저장될 때 암호화됩니다. <!-- AC-520 1323-->

* 영숫자가 아닌 파일 확장자의 업로드를 방지하기 위해 유효성 검사가 강화되었습니다. <!-- AC-479-->

* 이제 Adobe Commerce이 프로덕션 모드에 있으면 Swagger가 기본적으로 비활성화됩니다. <!-- AC-1450-->

* 이제 개발자는 엔드포인트별로 Adobe Commerce RESTful 엔드포인트에서 허용하는 배열에 대한 크기 제한을 구성할 수 있습니다. [API 보안](https://developer.adobe.com/commerce/webapi/get-started/api-security/)을 참조하십시오. <!-- AC-465-->

* 사용자가 웹 API를 통해 시스템 전체에서 요청할 수 있는 리소스의 크기 및 수를 제한하고 개별 모듈의 기본값을 재정의하기 위한 메커니즘을 추가했습니다. 이 개선 작업으로 `MC-43048__set_rate_limits__2.4.3.patch`에서 해결한 문제가 해결되었습니다. [API 보안](https://developer.adobe.com/commerce/webapi/get-started/api-security/)을 참조하십시오. <!-- AC-1120-->


## 2.4.3-p1

Adobe Commerce 2.4.3-p1 보안 릴리스는 이전 릴리스(Adobe Commerce 2.4.3 및 Magento Open Source 2.4.3)에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다. 이 릴리스에는 최신 보안 모범 사례를 준수하는 개선된 보안 기능도 포함되어 있습니다.


보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html)을 참조하십시오. 패치 릴리스에서는 공급업체가 개발한 [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://commercemarketplace.adobe.com//klarna-m2-klarna.html) 및 [Vertex](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html) 확장에 대한 버그 수정도 제공합니다.

### AC-3022.patch를 적용하여 DHL을 배송 운송업체로 계속 제공

DHL은 스키마 버전 6.2를 도입했으며 조만간 스키마 버전 6.0을 더 이상 사용하지 않을 예정입니다. DHL 통합을 지원하는 Adobe Commerce 2.4.4 및 이전 버전은 버전 6.0만 지원합니다. 이러한 릴리스를 배포하는 판매자는 가능한 한 빨리 `AC-3022.patch`을(를) 적용하여 DHL을 운송 회사로 계속 제공해야 합니다. 패치 다운로드 및 설치에 대한 자세한 내용은 [DHL을 계속 제공하려면 패치 적용](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) 기술 자료 문서를 참조하십시오.

### 핫픽스

이 릴리스에는 다음 핫픽스와 이전 패치 릴리스에 대해 릴리스된 모든 핫픽스가 포함됩니다.

* `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade` 패치입니다. 패치 및 문제에 대한 자세한 내용은 [Adobe Commerce 업그레이드 2.4.3, 2.3.7-p1 PHP 치명적 오류 핫픽스](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) 기술 자료 문서를 참조하십시오.

### 보안 주요 사항

**세션 ID가 데이터베이스에서 제거되었습니다**. 이 코드 변경으로 인해 상인이 데이터베이스에 저장된 원시 세션 ID를 사용하는 사용자 지정 또는 설치된 확장이 있는 경우 변경 사항이 중단될 수 있습니다. <!-- MC-40976-->

**미디어 갤러리 폴더에 대한 관리자 액세스를 제한했습니다**. 이제 기본 미디어 갤러리 권한에서는 구성에 의해 명시적으로 허용되는 디렉터리 작업(보기, 업로드, 삭제 및 만들기)만 허용합니다. 관리자 사용자는 `catalog/category` 또는 `wysiwyg` 디렉터리 외부에서 업로드된 미디어 갤러리를 통해 더 이상 미디어 자산에 액세스할 수 없습니다. 미디어 자산에 액세스하려는 관리자는 해당 미디어 자산을 명시적으로 허용된 폴더로 이동하거나 구성 설정을 조정해야 합니다. [미디어 라이브러리 폴더 권한 수정](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/)을 참조하십시오. <!-- B2B-1897-->

**GraphQL 쿼리 복잡성에 대한 제한을 낮춥니다**. DOS(서비스 거부) 공격을 방지하기 위해 GraphQL에서 허용하는 최대 쿼리 복잡성을 낮췄습니다. [GraphQL 보안 구성](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/)을 참조하십시오. <!-- PWA-1700-->

**최근 침투 테스트 취약점**&#x200B;이 이 릴리스에서 수정되었습니다. <!-- MC-42431-->

지원되지 않는 원본 식 `unsafe-inline`이(가) 콘텐츠 보안 정책 `frame-ancestors` 지시문에서 제거되었습니다. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
