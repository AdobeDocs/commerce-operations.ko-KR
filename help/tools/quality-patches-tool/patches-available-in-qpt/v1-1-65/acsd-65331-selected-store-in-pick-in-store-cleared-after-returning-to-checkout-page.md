---
title: 'ACSD-65331: 체크아웃으로 돌아간 후 [!UICONTROL Pick in Store]에서 선택한 저장소가 지워졌습니다.'
description: ACSD-65331 패치를 적용하여 사용자가 체크아웃 페이지로 반복적으로 돌아올 때 [!UICONTROL Pick In Store] 옵션 아래에 있는 선택한 저장소가 지워지는 Adobe Commerce 문제를 해결합니다.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: a322e822ccf0b584d2385d3f38a3b92ebe3a23d3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# ACSD-65331: 체크아웃으로 돌아간 후 **[!UICONTROL Pick in Store]**&#x200B;에서 선택한 저장소가 지워졌습니다.

ACSD-65331 패치는 사용자가 반복적으로 체크아웃 페이지로 돌아오면 **[!UICONTROL Pick In Store]** 옵션 아래에 있는 선택한 저장소가 지워지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65331입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 체크아웃 페이지로 반복적으로 돌아오면 **[!UICONTROL Pick In Store]** 옵션 아래에서 선택한 저장소가 지워집니다.

<u>재현 단계</u>:

1. **[!UICONTROL In-Store Delivery]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**(으)로 이동하여 **[!UICONTROL In-Store Delivery]**&#x200B;을(를) 사용하도록 설정합니다.
1. [!DNL Google] > [!UICONTROL Google Distance Provider] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]**(으)로 이동하여 **[!UICONTROL Inventory]**&#x200B;에 대한 올바른 **[!UICONTROL Google Distance Provider]** API 키를 구성하십시오.
1. 다음 세부 정보가 포함된 새 소스를 추가하려면 **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**(으)로 이동합니다.

   * **[!UICONTROL Latitude]**: *41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *예*
   * **[!UICONTROL Country]**: *미국*
   * **[!UICONTROL State]**: *일리노이*
   * **[!UICONTROL City]**: *캐롤 스트림*
   * **[!UICONTROL Street]**: *565E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. 새 주식을 만들려면 **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]**(으)로 이동합니다.

   새로 생성된 소스 및 기본 웹 사이트를 이 스톡에 할당합니다.
1. 모든 제품 편집 및:

   1. 새로 생성된 소스에 할당합니다.
   1. 상태를 *[!UICONTROL In Stock]*(으)로 설정하고 수량을 0보다 크게 설정합니다.

1. 리인덱서를 실행합니다.
1. 상점 첫 화면에서 새 고객을 만들고 캘리포니아 주소를 기본 청구 및 배송 주소로 설정합니다.
1. 동일한 고객에 일리노이 주소를 추가합니다(기본값이 아님).
1. 구성된 제품을 장바구니에 추가하고 **[!UICONTROL Checkout]**(으)로 진행합니다.
1. 일리노이 주소를 선택하고 배송 방법으로 **[!UICONTROL Pick In Store]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. 소스가 로드될 때까지 기다린 후 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. 홈페이지로 다시 이동합니다.
1. **[!UICONTROL Checkout]** 페이지를 다시 방문하십시오.

<u>예상 결과</u>:

선택한 스토어는 **[!UICONTROL Pick In Store]**&#x200B;에서 계속 사용할 수 있습니다.

<u>실제 결과</u>:

배송 단계가 로드되기 시작하고 **[!UICONTROL Pick In Store]**(으)로 리디렉션되지만 스토어가 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* [!DNL Quality Patches Tool] 안내서의 Adobe Commerce 또는 Magento Open Source 온-프레미스: [**&#x200B;** > 사용량][!DNL Quality Patches Tool]**(/help/tools/quality-patches-tool/usage.md).
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용]**(https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]**에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]&#x200B;**: 도구 안내서의 품질 패치용 셀프서비스 도구]**(/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
