---
title: 서비스 모범 사례 업데이트
description: 클라우드 인프라 기술 스택을 계속 업데이트하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# 서비스 모범 사례 업데이트

이 문서에서는 Adobe Commerce on cloud 인프라 기술 스택을 업데이트하도록 권장하는 사항을 제공하며 유용한 리소스에 대한 링크를 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure 2.4.x 이상

## 서비스 업데이트

Adobe Commerce에서 사용 중인 서비스와 구성 요소가 수명 종료 날짜에 도달하거나 가까워지기 전에 업그레이드하십시오. 따라서 PCI 규정을 준수하고 보안 취약점을 줄일 수 있습니다.

스타터 플랜을 사용하는 고객은 서비스 업그레이드에 대해 셀프 서비스를 제공할 수 있습니다. 을(를) 참조하십시오. [서비스 버전 변경](https://devdocs.magento.com/cloud/project/services.html#change-service-version) 를 참조하십시오.

Pro 플랜의 고객은 서비스 업그레이드에 대해서만 셀프 서비스를 제공할 수 있습니다 [통합 환경](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). 프로덕션에서 서비스를 업그레이드하려면 다음을 수행해야 합니다 [지원 티켓 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 업그레이드 요청.

>[!WARNING]
>
>서비스 업그레이드는 48시간의 업무 시간 동안 인프라 팀에 통보하지 않으면 운영 환경에 푸시될 수 없습니다. 이는 운영 환경에 대한 다운타임을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있는 인프라 지원 엔지니어가 있는지 확인해야 하기 때문입니다.

다음 파일에서 서비스 버전 및 사용 종료 날짜 목록을 볼 수 있습니다. [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>이 파일은 하나의 진실 소스로 간주할 수 없습니다. 확실하지 않은 경우 공식 공급업체 웹 사이트를 참조하십시오.

## 추가 정보

[시스템 요구 사항](../../../installation/system-requirements.md)
