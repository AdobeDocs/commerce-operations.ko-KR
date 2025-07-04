---
title: 'ACSD-64753: 스토어의 Pickup에서 미리 선택한 스토어는 배송 주소가 변경될 때 업데이트되지 않습니다'
description: ACSD-64753 패치를 적용하여 선택한 스토어의 서비스 반경 외부에 새 배송 주소를 입력할 때 사전 선택한 스토어가 업데이트되지 않은 Adobe Commerce 문제를 해결합니다.
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 036c1b81d9ec8f55f002446a8ea6078c6f8014d9
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-64753: 배송 주소가 변경될 때 &quot;Pickup in Store&quot;에서 미리 선택한 저장소가 업데이트되지 않음

ACSD-64753 패치는 선택한 스토어의 서비스 반경 밖에 새 배송 주소를 입력했을 때 사전 선택한 스토어가 업데이트되지 않았던 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64753입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

선택한 스토어의 서비스 반경 밖에 새 배송 주소를 입력해도 미리 선택한 스토어가 업데이트되지 않았습니다.

<u>재현 단계</u>:

1. **[!UICONTROL In-Store Delivery]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**(으)로 이동하여 **[!UICONTROL In-Store Delivery]**&#x200B;을(를) 사용하도록 설정합니다.
1. [!DNL Google]에 대한 올바른 [!DNL Google Distance Provider] API 키를 제공하십시오. 이렇게 하려면 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**(으)로 이동합니다.
1. 새 소스(**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**)를 추가하고 다음 값을 설정하십시오.
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *예*
   * **[!UICONTROL Country United]**: *상태*
   * **[!UICONTROL State]**: *일리노이*
   * **[!UICONTROL City]**: *캐롤 스트림*
   * **[!UICONTROL Postcode]**: *60188*
1. 새 재고(**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**)를 추가하고 새 소스와 기본 웹 사이트를 할당합니다.
1. 제품을 편집하고, 새 Source에 제품을 할당하십시오. 재고 및 수량은 > *0*&#x200B;입니다.
1. 색인 재지정이 완료될 때까지 기다립니다.
1. 상점에서 새 고객을 만든 다음 캘리포니아 주소를 기본 청구 및 배송으로 추가합니다.
1. 이 고객에게 기본이 아닌 다른 일리노이 주소를 추가합니다.
1. 제품을 장바구니에 추가하고 체크아웃을 진행합니다.
1. 캘리포니아 배송 주소를 선택한 상태로 두고 **[!UICONTROL Pick in Store]** 배송 방법을 선택하십시오. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

캘리포니아 주소는 최대 검색 반경(200km) 밖에 있으므로 고객이 일리노이 Source을 사용할 수 없습니다.

<u>실제 결과</u>:

일리노이 출처를 선정하고 고객이 체크아웃을 진행할 수 있다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
