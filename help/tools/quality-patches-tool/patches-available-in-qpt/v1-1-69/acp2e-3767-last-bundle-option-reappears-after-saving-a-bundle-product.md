---
title: 'ACP2E-3767: 번들 제품을 저장한 후 마지막 번들 옵션이 다시 나타납니다'
description: ACP2E-3767 패치를 적용하여 번들 제품의 마지막 번들 옵션을 제거할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767: 번들 제품을 저장한 후 마지막 번들 옵션이 다시 나타납니다

ACP2E-3767 패치는 번들 제품을 저장한 후 마지막 번들 옵션이 다시 나타나는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3767입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

번들 제품의 마지막 번들 옵션은 제거할 수 없습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**(으)로 이동합니다.
1. 드롭다운에서 **[!UICONTROL Simple Product]**&#x200B;을(를) 선택합니다.
1. 필요한 데이터를 입력하고 저장합니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**(으)로 이동합니다.
1. 드롭다운에서 **[!UICONTROL Bundle Product]**&#x200B;을(를) 선택합니다.
1. 필요한 데이터를 입력합니다.
1. 번들 항목에서 **[!UICONTROL Add Option]**&#x200B;을(를) 클릭합니다.
1. 새 옵션에 제목을 추가한 다음 **[!UICONTROL Add Products to Option]**&#x200B;을(를) 클릭합니다.
1. 이전에 만든 간단한 제품을 선택한 다음 **[!UICONTROL Add Selected Products]**&#x200B;을(를) 선택합니다.
1. 번들 제품을 저장합니다.
1. 번들 옵션을 제거하고 저장합니다.

<u>예상 결과</u>:

1. 번들 옵션이 제거되었습니다.
1. 제거가 허용되지 않으면 메시지가 표시됩니다.

<u>실제 결과</u>:

1. 번들 옵션은 활성 상태로 유지됩니다.
1. 오류나 알림이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
