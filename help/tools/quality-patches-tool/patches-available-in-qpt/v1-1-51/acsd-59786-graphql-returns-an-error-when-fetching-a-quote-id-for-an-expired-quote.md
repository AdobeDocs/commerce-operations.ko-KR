---
title: 'ACSD-59786: GraphQL이 만료된 견적에 대해 ''quote_id''를 가져오는 도중 오류 반환'
description: ACSD-59786 패치를 적용하여 GraphQL 쿼리가 만료된 견적에 대해 'quote_id'를 가져올 때 오류를 반환하는 Adobe Commerce 문제를 수정합니다.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786: GraphQL이 만료된 견적에 대해 `quote_id`을(를) 가져올 때 오류를 반환합니다.

ACSD-59786 패치는 만료된 견적에 대해 `quote_id`을(를) 가져올 때 GraphQL 쿼리가 오류를 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-59786입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 쿼리에서 만료된 견적에 대한 `quote_id`을(를) 가져오는 동안 오류가 반환되었습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Companies]** 및 **[!UICONTROL Purchase Orders]**&#x200B;을(를) 사용하도록 설정합니다.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**(으)로 설정하고 **[!UICONTROL Enable Company]**&#x200B;을(를) *예*(으)로 설정합니다.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]**(으)로 설정하고 **[!UICONTROL Enable Purchase Orders]**&#x200B;을(를) *예*(으)로 설정합니다.
1. 새 회사를 만들고 동일한 회사에 대해 **[!UICONTROL Enable Purchase Orders]**&#x200B;을(를) *예*(으)로 설정합니다.
1. 간단한 제품을 만들고 카테고리에 할당합니다.
1. 회사 관리자 계정을 사용하여 Storefront에 로그인하고 **[!UICONTROL Purchase Order]**&#x200B;을(를) 결제 방법으로 사용하여 새 주문을 만듭니다.
1. **[!UICONTROL Quote Lifetime (days)]**&#x200B;을(를) 변경합니다.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. `bin/magento c:f` 명령을 실행합니다.
1. DB `quote_table`(으)로 이동하여 `created_at` 및 `updated_at` 값을 하루 전에 변경합니다.
1. `bin/magento cron:run --group="sales_clean_quotes` 명령을 실행합니다.
1. **[!UICONTROL Purchase Order]**&#x200B;을(를) 만드는 관리자를 위해 승인된 토큰을 사용하여 아래에 지정된 GraphQL 요청을 실행하십시오.

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>예상 결과</u>:

GraphQL 쿼리가 `quote_id`을(를) 반환합니다.

<u>실제 결과</u>:

GraphQL 쿼리가 내부 서버 오류를 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
