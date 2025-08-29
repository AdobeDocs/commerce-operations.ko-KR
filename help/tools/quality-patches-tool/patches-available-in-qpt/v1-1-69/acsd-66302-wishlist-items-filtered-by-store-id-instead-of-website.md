---
title: 'ACSD-66302: 웹 사이트 대신 스토어 ID로 필터링된 위시리스트 항목'
description: ACSD-66302 패치를 적용하여 위시리스트 항목이  [!DNL GraphQL] 요청에서 웹 사이트 대신 스토어 ID로 필터링되는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: c1a9eadc-0321-4f5c-ba82-533286a1f24f
source-git-commit: bec27df19ce5d34be063dce3de74ffe253c3e8f4
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-66302: 웹 사이트 대신 스토어 ID로 필터링된 위시리스트 항목

ACSD-66302 패치는 [!DNL GraphQL] 요청에서 웹 사이트 대신 스토어 ID로 위시리스트 항목을 필터링하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66302입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

위시리스트 항목이 웹 사이트가 아닌 스토어 ID로 잘못 필터링됩니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 추가 스토리를 만듭니다.
1. 관리에서 **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]**(으)로 이동한 다음 **[!UICONTROL Enable Multiple Wish Lists]**&#x200B;을(를) `Yes`(으)로 설정합니다.
1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**(으)로 이동한 다음 **[!UICONTROL Add Store Code to Urls]**&#x200B;을(를) `Yes`(으)로 설정합니다.
1. 고객 계정을 만듭니다.
1. [!DNL GraphQL] 요청을 사용하여 고객 인증 토큰을 검색하십시오.
1. 고객으로 로그인합니다.
1. **[!UICONTROL Default Store View]**&#x200B;을(를) 선택하고 제품을 위시리스트에 추가하십시오.
1. 저장소 보기를 *test*(으)로 전환합니다.
1. 제품이 여전히 위시리스트에 표시되는지 확인합니다(올바른 동작).
1. 다음 [!DNL GraphQL] 쿼리를 실행합니다.

   ```
   {
     customer {
       wishlists {
         id
         name
         items_count
         items_v2 {
           items {
             id
             product {
               uid
               name
               sku
             }
           }
         }
       }
     }
   }
   ```

1. 기본 스토어에서 쿼리를 수행합니다. 제품이 예상대로 표시됩니다.
1. 테스트 저장소에서 동일한 쿼리를 수행합니다. 제품이 표시되지 않습니다.

<u>예상 결과</u>:

[!DNL GraphQL] 쿼리를 통해 동일한 웹 사이트 내의 모든 스토어 보기에서 제품을 볼 수 있어야 합니다.

<u>실제 결과</u>:

스토어 조회수를 전환할 때 제품이 위시리스트에서 사라집니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
