---
title: 품질 패치 도구로 Adobe Commerce 패치 문제 확인
description: 이 문서에서는 QPT(Quality Patches Tool)에 대한 개요와 사용 방법을 설명하는 리소스 링크를 제공합니다.
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%
---
# 품질 패치 도구로 Adobe Commerce 패치 문제 확인

이 문서에서는 QPT(Quality Patches Tool)에 대한 개요와 사용 방법을 설명하는 리소스 링크를 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스, 모든 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 품질 패치 도구란 무엇입니까?

[품질 패치 도구](https://github.com/magento/quality-patches)&#x200B;(QPT)는 Adobe 및 Magento Open Source 커뮤니티에서 개발한 개별 패치입니다.

이를 통해 다음을 수행할 수 있습니다.

* 패키지에 포함된 품질 패치 적용
* 이전에 적용된 패치 되돌리기
* 설치된 버전의 Adobe Commerce에 사용할 수 있는 품질 패치에 대한 일반 정보를 봅니다.

다음은 사용 가능한 패치를 보기 위해 얻을 수 있는 상태 테이블의 예입니다.

![사용 가능한 패치와 설치 상태를 보여주는 품질 패치 도구 상태 테이블](/help/assets/tools/status_table.png)

이 도구는 Adobe Commerce에서 발생할 수 있는 문제에 대한 패치를 자체 서비스하거나 Adobe Commerce 지원에서 제안한 패치를 쉽게 적용할 수 있도록 하기 위한 것입니다.

>[!NOTE]
>
>QPT는 품질 패치용으로만 사용됩니다. 보안 패치는 [Magento 보안 센터](/help/release/release-notes/overview.md)에서 사용할 수 있습니다.

## 품질 패치 도구에서 사용할 수 있는 패치

사용 가능한 패치 목록은 개발자 설명서에서 [품질 패치 도구](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.

## 품질 패치 도구 설치 및 사용 방법

Adobe Commerce 온프레미스 및 Adobe Commerce 온클라우드 인프라의 경우 ece-tools 패키지에 QPT 패키지가 포함되므로 설치 및 사용 명령이 다릅니다.

### Adobe Commerce 온프레미스용 QPT를 설치하고 사용하는 방법

패치를 적용하고 되돌리기 위해 QPT를 설치하고 사용하는 방법에 대한 자세한 내용은 개발자 설명서에서 [소프트웨어 업데이트 안내서 > 패치](/help/tools/quality-patches-tool/usage.md)를 참조하십시오.

### 클라우드 인프라에서 Adobe Commerce용 QPT를 설치하고 사용하는 방법

클라우드 인프라에서 Adobe Commerce에 패치를 적용하고 되돌리기 위해 QPT를 설치하고 사용하는 방법에 대한 자세한 내용은 개발자 설명서에서 [Adobe Commerce용 클라우드 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)을 참조하십시오.

## 관련 읽기

* 개발자 설명서에서 [품질 패치 도구 릴리스 노트](/help/tools/quality-patches-tool/release-notes.md).
* 지원 기술 자료에서 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento).
