---
title: Adobe Commerce 2.4.2 보안 패치 릴리스 노트
description: Adobe Commerce 버전 2.4.2의 보안 패치 릴리스에 포함된 보안 버그 수정, 보안 개선 사항 및 기타 보안 관련 업데이트에 대해 알아봅니다.
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: d532402e2d65a1f34558fc3c283d4291be5b006b
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Adobe Commerce 2.4.2 보안 패치 릴리스 노트

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.2-p2

Adobe Commerce 2.4.2-p2 보안 릴리스는 이전 릴리스 2.4.2에서 식별된 취약점에 대한 보안 버그 수정 사항을 제공합니다.

보안 버그 수정에 대한 최신 정보는 [Adobe 보안 게시판 APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html)을 참조하십시오.

## `AC-3022.patch`을(를) 적용하여 DHL을 배송 운송업체로 계속 제공

DHL은 스키마 버전 6.2를 도입했으며 조만간 스키마 버전 6.0을 더 이상 사용하지 않을 예정입니다. DHL 통합을 지원하는 Adobe Commerce 2.4.4 및 이전 버전은 버전 6.0만 지원합니다. 이러한 릴리스를 배포하는 판매자는 가능한 한 빨리 `AC-3022.patch`을(를) 적용하여 DHL을 운송 회사로 계속 제공해야 합니다. 패치 다운로드 및 설치에 대한 자세한 내용은 [DHL을 계속 제공하려면 패치 적용](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) 기술 자료 문서를 참조하십시오.
