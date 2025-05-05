---
title: 'ACSD-63883: [!UICONTROL Requisition List]에 대한  [!DNL GraphQL] 응답에서 잘못된 ''items_count''를 수정하는 중'
description: ACSD-63883 패치를 적용하여 [!UICONTROL Requisition List]이(가)  [!DNL GraphQL] 응답에서 잘못된 'items_count'를 반환하는 문제를 해결합니다.
feature: B2B, GraphQL
role: Admin, Developer
source-git-commit: 5d8b78588b11534828a9b925cbab0cc945860367
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883: [!UICONTROL Requisition List]에 대한 [!DNL GraphQL] 응답에서 잘못된 `items_count`을(를) 수정하는 중

ACSD-63883 패치는 **[!UICONTROL Requisition List]**&#x200B;이(가) [!DNL GraphQL] 응답에서 잘못된 `items_count`을(를) 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63883입니다. 이 문제는 Adobe Commerce B2B 1.5.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Requisition List]**&#x200B;이(가) [!DNL GraphQL] 응답에서 잘못된 `items_count`을(를) 반환합니다.


<u>재현 단계</u>:

1. B2B **[!UICONTROL Requisition List]** 기능을 사용하도록 설정합니다.
1. 몇 가지 제품을 만듭니다.
1. 고객 계정을 만듭니다.
1. **[!UICONTROL Create new Requisition List]**&#x200B;을(를) 클릭합니다.
1. `addProductsToRequisitionList` [!DNL GraphQL] 돌연변이 요청을 제품과 함께 보내 [!UICONTROL Requisition List]에 추가합니다.

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. [!UICONTROL Requisition List]에 추가하려면 다른 세 제품과 함께 `addProductsToRequisitionList` [!DNL GraphQL] 돌연변이 요청을 보냅니다.
1. 응답에서 `items_count`을(를) 확인합니다.

**예상 결과**:

* `items_count`: 응답에서 4가 반환되어야 합니다.

**실제 결과**:

* `items_count`: 응답에서 2가 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
