---
title: Adobe Commerce 2.4.7 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.7의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Adobe Commerce 2.4.7 보안 패치 릴리스 노트

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Adobe Commerce 2.4.7-p1 보안 릴리스는 이전 릴리스 2.4.7에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 다음을 참조하십시오. [Adobe 보안 게시판 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### 보안 주요 사항

* **업데이트 [일회용 암호(OTP) 설정](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) Google Authenticator**-에서 도입한 오류를 해결하려면 이 업데이트가 필요합니다. [역호환변화](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) 2.4.7. 다음에 대한 설명 **[!UICONTROL OTP Window]** 이제 필드에서 설정에 대한 정확한 설명을 제공하고 기본값이 다음에서 변경되었습니다. `1` 끝 `29`.

* **B2B 버전 호환성**—Commerce 버전 2.4.7-p1과의 호환성을 위해 Adobe Commerce B2B 확장 기능이 있는 판매자는 로 업그레이드해야 합니다. [B2B 버전 1.4.2-p1](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).

### 이 릴리스에 포함된 핫픽스

Adobe Commerce 2.4.7-p1은 SOAP에서 REST API로 UPS 통합 마이그레이션 범위에서 도입된 문제를 해결합니다. 이 문제는 미국 외에서 배송하는 고객에게 영향을 미쳐 UPS로 배송을 생성하는 포장물에 킬로그램 및 센티미터의 지표 시스템/SI 측정을 사용할 수 없게 했습니다. 다음을 참조하십시오. [SOAP에서 RESTful API로 UPS 배송 방법 통합 마이그레이션](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) 자세한 내용은 기술 자료 문서를 참조하십시오.
