---
title: 'ACSD-61667: 배송 생성을 위한 재고 성과 향상'
description: ACSD-60584 패치를 적용하여 매장 내 픽업이 많은 소스의 경우 배송을 위한 재고 성능을 향상시킬 수 있습니다.
feature: Customers, Shipping/Delivery
role: Admin, Developer
source-git-commit: 29748a439992c0e3efbbc84c5ab9c8239f460b73
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: 출하 생성을 위한 재고 성과 향상

ACSD-61667 패치는 [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)(이전 MSI) 픽업 스토어에서 여러 소스를 사용할 수 있게 되면 판매자가 주문을 배달할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61667입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 원본과 함께 MSI 픽업 스토어가 활성화된 경우 주문을 배송할 수 없습니다. 이 패치는 매장 내 픽업이 많은 소스의 경우 배송을 만들기 위해 재고 성능을 향상시킵니다.

<u>필수 구성 요소:</u>:

Adobe Commerce 인벤토리 모듈이 설치되고 활성화됩니다.

<u>재현 단계</u>:

1. *10*&#x200B;개 이상의 소스를 만들고 픽업 위치를 사용하도록 설정합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;에서 Pickup Store를 사용할 수 있습니다.
1. 대량의 픽업 주문을 만듭니다.
1. **[!UICONTROL Admin login]**(으)로 이동하여 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**&#x200B;을(를) 선택합니다.
1. 보류 중인 주문을 필터링하고 확인합니다.
1. **[!UICONTROL Ship]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

배송 페이지가 예상대로 로드됩니다.

<u>실제 결과</u>:

*503 최대 실행 시간이 초과되었습니다* 오류가 발생했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).

