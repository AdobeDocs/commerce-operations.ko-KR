---
title: 'ACSD-65777: ''MediaGallery'' GraphQL 요청에 제품 이미지 유형에 대한 "유형" 필드가 누락됨'
description: ACSD-65777 패치를 적용하여 'MediaGallery' GraphQL 요청의 제품 이미지 유형에 대한 "유형" 필드가 누락되는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4f0ac23d70eed6d2ea0441d4c8aa8cfc3138ff04
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACSD-65777: **[!UICONTROL types]** GraphQL 요청에 제품 이미지 형식에 대한 `MediaGallery` 필드가 누락되었습니다.

ACSD-65777 패치는 **[!UICONTROL types]** GraphQL 요청의 제품 이미지 유형에 대해 `MediaGallery` 필드가 누락되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65777입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL types]** GraphQL 요청을 통해 미디어 데이터를 가져오는 동안 제품 이미지 유형에 대한 `MediaGallery` 필드가 누락되었습니다.

<u>재현 단계</u>:

1. 제품을 만듭니다.
1. 제품에 이미지를 업로드합니다.
1. 다음 GraphQL을 사용하여 미디어 데이터를 가져옵니다.

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>예상 결과</u>:

`media_gallery` GraphQL 인터페이스에는 **[!UICONTROL types]** 필드가 포함되어야 합니다.

<u>실제 결과</u>:

`media_gallery`에 미디어 **[!UICONTROL types]** 필드가 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
