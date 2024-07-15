---
title: 서비스 모범 사례 업데이트
description: Adobe Commerce on cloud infrastructure 기술 스택을 업데이트하도록 유지하는 방법에 대해 알아봅니다.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# 서비스 모범 사례 업데이트

이 문서에서는 클라우드 인프라 기술 스택에 대한 Adobe Commerce의 업데이트 유지에 대한 권장 사항을 제공하고 유용한 리소스에 대한 링크를 제공합니다.

## 영향을 받는 제품 및 버전

cloud infrastructure 2.4.x 이상 버전의 Adobe Commerce

## 서비스 업데이트

Adobe Commerce에서 사용하는 서비스 및 구성 요소가 수명 종료 날짜에 도달하거나 임박하기 전에 업그레이드하십시오. 따라서 PCI 규정 준수를 준수하고 보안 취약점을 줄일 수 있습니다.

Starter 플랜을 사용하는 고객은 서비스 업그레이드에 셀프 서비스를 사용할 수 있습니다. 자세한 방법은 [서비스 버전 변경](https://devdocs.magento.com/cloud/project/services.html#change-service-version)을 참조하세요.

Pro 요금제의 고객은 [통합 환경](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html)에서 서비스 업그레이드에서만 셀프 서비스를 사용할 수 있습니다. 프로덕션에서 서비스를 업그레이드하려면 [지원 티켓을 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)하여 업그레이드를 요청해야 합니다.

>[!WARNING]
>
>서비스 업그레이드는 48시간 내에 인프라 팀에 통지하지 않으면 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다.

[https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml) 파일에서 서비스 버전 및 서비스 종료 날짜 목록을 볼 수 있습니다.

>[!NOTE]
>
>이 파일은 신뢰할 수 있는 단일 소스로 간주할 수 없습니다. 이러한 기술에 대한 공식 공급업체 웹 사이트를 참조하십시오.

## 추가 정보

[시스템 요구 사항](../../../installation/system-requirements.md)
