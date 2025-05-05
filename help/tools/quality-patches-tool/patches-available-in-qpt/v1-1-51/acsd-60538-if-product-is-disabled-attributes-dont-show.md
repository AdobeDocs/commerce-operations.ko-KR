---
title: 'ACSD-60538: [!UICONTROL All Store Views]에서 제품을 사용하지 않도록 설정한 경우 특성이 올바르게 표시되지 않습니다.'
description: ACSD-60538 패치를 적용하여 제품이 *모든 스토어 보기*에서 비활성화되고 특정 스토어 보기 범위에서만 활성화되는 경우 제품 속성이 GraphQL 응답에 올바르게 표시되지 않아 제품이 제대로 표시되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538: *[!UICONTROL All Store Views]*&#x200B;에서 제품을 사용하지 않도록 설정한 경우 특성이 올바르게 표시되지 않습니다.

ACSD-60538 패치는 *[!UICONTROL All Store Views]*&#x200B;에서 제품을 사용하지 않도록 설정하고 특정 스토어 보기 범위에서만 사용하도록 설정한 경우 GraphQL 응답에 제품 특성이 올바르게 표시되지 않아서 제품이 제대로 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-60538입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 *[!UICONTROL All Store Views]*&#x200B;에서 비활성화되고 특정 스토어 보기 범위에서만 활성화된 경우 제품 특성이 GraphQL 응답에 올바르게 표시되지 않아서 제품이 제대로 표시되지 않습니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. *color* 특성과 세 가지 하위 제품(*파랑*, *검정*, *갈색*)을 사용하여 구성 가능한 제품을 만드십시오.
1. *[!UICONTROL All Store Views]* 범위에서 두 개의 연결된 하위 제품(*파란색* 및 *검정*)을 사용하지 않도록 설정하십시오.
1. **[!UICONTROL Store View]** 범위로 이동합니다.
1. *[!UICONTROL Store View]* 범위에서 하위 제품(*파란색* 및 *검정*)을 사용하도록 설정합니다.
1. 아래 GraphQL 요청을 실행합니다.

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>예상 결과</u>:

GraphQL 응답에는 *[!UICONTROL All Store Views]*&#x200B;에서 비활성화되고 *[!UICONTROL Store View]* 범위에서 활성화된 하위 관련 제품에 대한 특성 값이 포함됩니다.

<u>실제 결과</u>:

*[!UICONTROL All Store Views]*&#x200B;에서 제품을 사용하지 않도록 설정하고 *[!UICONTROL Store View]* 범위에서 사용하도록 설정한 경우 GraphQL 응답에 하위 관련 제품에 대한 특성 값이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
