---
title: 'ACP2E-3689: 카테고리 트리와 관련된 여러 문제가 더 깊은 수준에 표시되고 앵커/비 앵커 관계가 반영됩니다'
description: ACP2E-3689 패치를 적용하여 깊이 4 이상의 중첩에 카테고리 트리가 표시되고 앵커/비앵커 관계가 반영되는 Adobe Commerce 문제를 해결합니다.
feature: Categories, Page Content
role: Admin, Developer
exl-id: 8d3c484f-3f8d-4fc1-8b31-e850cb34341c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACP2E-3689: 카테고리 트리와 관련된 여러 문제가 더 깊은 수준에 표시되고 앵커/비 앵커 관계가 반영됩니다

>[!NOTE]
>
>이 패치는 버전 2.4.7 이상의 [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md)을(를) 대체합니다.

ACP2E-3689 패치는 깊이 4 이상의 중첩과 앵커/비앵커 관계의 반영에 카테고리 트리 표시와 관련된 여러 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3689입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

더 깊은 수준(4+)의 범주 트리가 올바르게 표시되지 않고 앵커/비 앵커 관계를 반영합니다.

<u>재현 단계</u>:

1. 4개 수준 이상의 중첩된 범주가 있는 범주 트리를 설정하십시오.
1. 다른 위치에 표시되는 관리자의 범주 트리를 확장합니다.
   1. [!UICONTROL Related Products Rule]을(를) 설정하고 범주를 기준으로 조건을 설정합니다.
   1. 위젯을 만들고 [!UICONTROL Layout Updates]에서 [!UICONTROL Anchor categories]을(를) 선택합니다.

<u>예상 결과</u>:

범주 트리의 모든 수준이 올바르게 표시됩니다.

<u>실제 결과</u>:

카테고리 트리의 처음 몇 수준(&lt;4)만 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
