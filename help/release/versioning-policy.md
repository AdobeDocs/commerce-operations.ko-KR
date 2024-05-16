---
title: 릴리스 정책
description: 부, 패치, 보안 패치, 기능, 핫픽스, 개별 패치 및 사용자 정의 패치를 포함한 다양한 유형의 Adobe Commerce 릴리스에 대해 알아봅니다.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Adobe Commerce 릴리스 정책

Adobe Commerce 사용 [시맨틱 버전 관리](https://semver.org/) 개별 모듈 수준에서(예: `magento/framework 101.1.1`)를 사용할 수 있지만 마케팅 버전 번호에는 사용할 수 없습니다. For example:

- **주요 릴리스**- 2
- **마이너 릴리스**—2.4
- **PATCH 릴리스**—2.4.5
   - **보안 패치 릴리스**—2.4.5-p1
      - 보안 버그 수정
      - 향상된 보안
- **베타 패치 릴리스**—2.4.7-Beta2
- **확장성, 인프라 및 서비스 릴리스**
- **핫픽스**
- **개별 패치**
- **사용자 정의 패치**

## 마이너 릴리스

부 릴리스에는 다음 지침이 적용됩니다.

- 변경할 수 있습니다. Adobe Commerce 2.2.x용으로 작성된 코드는 더 이상 Adobe Commerce 2.3.x에서 작동하지 않을 수 있습니다. 예를 들어 마이너 릴리스에서는 PHP와 같은 주요 시스템 요구 사항과 종속성에 대한 지원이 도입될 수 있습니다.
- 모듈 버전은 다를 수 있습니다. 예를 들어 일부 모듈 변경 사항은 새 패치에 도입되지만 다른 변경 사항은 작은 릴리스에 도입됩니다.
- 마이너 릴리스에는 호환성을 보장하기 위해 업그레이드 중에 사용자 또는 솔루션 파트너가 추가 작업을 수행해야 하는 새로운 기능이 포함될 수 있습니다.
- 마이너 릴리스에는 보안 및 품질 문제에 대한 수정 사항이 포함될 수 있습니다.

## PATCH 릴리스

패치 릴리스는 주로 보안, 성능, 규정 준수 및 높은 우선 순위의 품질 수정 사항을 제공하여 사이트의 성능을 최고로 유지하는 데 중점을 둡니다.

패치 릴리스에는 다음 지침이 적용됩니다.

- 최신 지원 마이너 릴리스에는 모든 기능 품질 수정 및 개선 사항이 적용됩니다.
- 확장이나 코드 호환성을 손상시킬 수 있는 변경 사항은 피합니다. 예를 들어 버전 2.2.0용으로 작성된 코드는 버전 2.2.7에서 계속 작동해야 합니다.
- 예외적으로 보안 또는 규정 준수 문제 및 영향력이 큰 품질 문제를 해결하기 위해 변경 사항이 있거나 추가 패치 또는 핫픽스가 릴리스될 수 있습니다. 모듈 수준에서 이는 대부분 PATCH 수준의 변경이며 경우에 따라 MINOR 수준의 변경입니다.

### 보안 패치 릴리스

{{$include /help/_includes/security-patch-release-overview.md}}

## 베타 패치 릴리스

Adobe Commerce 기능의 GA 전 릴리스는 모든 Adobe Commerce 고객 및 Adobe 파트너가 공개적으로 사용할 수 있습니다. 이를 통해 일반 공급 전에 코드 및 영향을 받는 구성 요소를 검토할 수 있습니다.

베타 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 지원(Adobe 지원 서비스 등을 통해)할 의무가 없습니다. 고객은 베타 릴리스 및/또는 관련 설명서나 자료의 올바른 기능이나 성능에 어떠한 의존도 하지 말고 주의하는 것이 좋습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

## 확장성, 인프라 및 서비스 릴리스

패치 릴리스와 별도로 독립 서비스로 제공되는 새로운 기능 및 기능 업데이트가 포함된 기능 릴리스. 예를 들면 API Mesh 및 Eventing과 같은 확장성 기술, Product Recommendations 및 Live Search와 같은 SaaS 제품, B2B 및 PWA Studio과 같은 독립 모듈, 클라우드 호스팅 서비스 및 인프라에 대한 업데이트 등이 있습니다.

## 핫픽스

핫픽스는 영향력이 큰 보안 또는 품질 수정 사항(예: 제로데이 취약점에 대한 수정 사항)이 포함되어 있는 패치로, 많은 판매자에게 영향을 줍니다. Adobe은 필요한 경우 여전히 지원되며 중요한 보안 또는 품질 문제의 영향을 받는 Adobe Commerce 버전에 대한 핫픽스를 릴리스합니다. 핫픽스가 다음에 게시됨 [알려진 문제 섹션](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 기술 자료. 이러한 수정 사항은 다음에 계획된 패치 릴리스에 포함되어 있습니다.

>[!NOTE]
>
>핫픽스에는 이전 버전과 호환 불가능한 변경 사항이 포함될 수 있습니다.

## 개별 패치

개별 패치에는 특정 문제에 대한 영향이 적은 품질 수정 사항이 포함되어 있습니다. 이러한 수정 사항은 지원되는 Adobe Commerce 부 버전에 적용됩니다. Adobe은 필요에 따라 Adobe Commerce에 대해 개별 패치를 릴리스합니다 [소프트웨어 수명 주기 정책](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>개별 패치에는 이전 버전과 호환 불가능한 변경 사항이 포함되어 있지 않습니다.

## 사용자 정의 패치

문제를 수정하거나 다양한 이유로 Adobe Commerce 코드를 수정하기 위해 Adobe이 아닌 사용자가 작성합니다. 사용자 정의 패치는 [품질 패치 도구](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## 관련 항목

- [버전 관리](https://developer.adobe.com/commerce/php/development/versioning/)
- [예정된 릴리스](schedule.md)
- [소프트웨어 수명 주기 정책](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
