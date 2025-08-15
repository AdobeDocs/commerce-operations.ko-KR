---
title: '[!DNL ACSD-47280]: 공유 카탈로그를 사용하지 않도록 설정하면 잘못된 제품 검색 결과가 나옵니다'
description: 공유 카탈로그 기능을 사용하지 않도록 설정한 경우 올바른 검색 결과를 표시하려면  [!DNL ACSD-47280] 패치를 적용하십시오.
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# [!DNL ACSD-47280]: 공유 카탈로그를 사용하지 않도록 설정하면 잘못된 제품 검색 결과가 나옵니다

[!DNL ACSD-47280] 기능을 사용하지 않도록 설정하면 [!DNL shared catalog] 패치가 올바른 검색 결과를 표시합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22가 설치된 경우에 사용할 수 있습니다. [!DNL patch ID]은(는) [!DNL ACSD-47280]입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). [!DNL patch ID]을(를) 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL shared catalog]을(를) 사용하지 않도록 설정하면 잘못된 제품 검색 결과가 표시됩니다.

<u>필수 구성 요소</u>:

* [!DNL B2B]개 모듈이 설치됨

<u>재현 단계</u>:

1. 두 번째 웹 사이트를 만듭니다.
1. 두 번째 웹 사이트에 제품을 할당합니다.
1. **을(를) 사용하여**&#x200B;초 웹 사이트[!DNL GraphQL]에서 제품 확인:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. 기본 **[!UICONTROL Shared Catalog]**&#x200B;에서 [!DNL scope]을(를) 사용하도록 설정합니다.
1. [!DNL GraphQL] 요청에 더 이상 두 번째 웹 사이트에 대한 제품이 표시되지 않습니다. 이는 올바른 결과입니다.
1. 두 번째 웹 사이트의 [!DNL scope]&#x200B;(으)로 이동하여 **[!UICONTROL Company]**&#x200B;을(를) 비활성화합니다.

<u>예상 결과</u>:

[!DNL GraphQL] 요청에도 두 번째 웹 사이트에 대한 제품이 표시됩니다.

<u>실제 결과</u>:

[!DNL GraphQL] 요청에 두 번째 웹 사이트에 대한 제품이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
