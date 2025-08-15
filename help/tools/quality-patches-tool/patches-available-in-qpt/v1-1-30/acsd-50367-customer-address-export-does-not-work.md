---
title: 'ACSD-50367: 고객 주소 내보내기가 다중 선택 특성과 함께 작동하지 않음'
description: 값이 없는 다중 선택 **&grave;고객 주소&grave;** 속성이 생성될 때 고객 주소 내보내기가 작동하지 않는 Adobe Commerce 문제를 해결하려면 ACSD-50367 패치를 적용합니다.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-50367: 고객 주소 내보내기가 작동하지 않음

ACSD-50367 패치는 값이 없는 다중 선택 **`Customer Address`** 특성을 만들 때 고객 주소 내보내기가 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-50367입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

값이 없는 다중 선택 **`Customer Address`** 특성이 만들어지면 고객 주소 내보내기가 작동하지 않습니다.

<u>필수 구성 요소</u>:

주소를 사용하여 고객을 만듭니다.

<u>재현 단계</u>:

1. **`Customer Address`** > **[!UICONTROL Admin]** > **[!UICONTROL Stores]**&#x200B;에서 다중 선택 **[!UICONTROL Customer Addresses]** 특성을 만듭니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**(으)로 이동한 다음 **`Customer Address`** 엔터티 형식을 선택합니다.
1. 고객 주소를 내보냅니다. 내보내는 항목이 없습니다.
1. 다중 선택 **`Customer Address`** 특성을 삭제하고 고객 주소를 다시 내보냅니다. 이번에는 주소의 CSV 파일이 생성됩니다.

<u>예상 결과</u>:

다중 선택 **`Customer Address`** 특성을 만들 때 고객 주소를 CSV 파일로 내보낼 수 있습니다.

<u>실제 결과</u>:

다중 선택 **`Customer Address`** 특성을 만들 때 고객 주소를 CSV 파일로 내보낼 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
