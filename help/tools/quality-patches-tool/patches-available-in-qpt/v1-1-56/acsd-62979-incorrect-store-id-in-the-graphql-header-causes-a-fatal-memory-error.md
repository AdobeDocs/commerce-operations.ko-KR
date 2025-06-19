---
title: 'ACSD-62979: GraphQL 헤더의 잘못된 스토어 ID로 인해 치명적인 메모리 오류가 발생합니다'
description: ACSD-62979 패치를 적용하여 GraphQL 헤더에서 잘못된 스토어 ID를 사용하면 치명적인 메모리 오류가 발생하는 Adobe Commerce 문제를 해결합니다
feature: GraphQL
role: Admin, Developer
exl-id: 832baae1-34b4-4ca8-bfa9-221aa60da67e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-62979: GraphQL 헤더의 잘못된 스토어 ID로 인해 치명적인 메모리 오류가 발생합니다

ACSD-62979 패치는 GraphQL 헤더에서 잘못된 스토어 ID를 사용하면 치명적인 메모리 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62979입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6, 2.4.6-p7, 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 헤더에서 잘못된 스토어 ID를 사용하면 치명적인 메모리 오류가 발생하는 문제를 해결했습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**(으)로 이동합니다. **[!UICONTROL Add Store Code to Urls]** 사용
1. 스토어 헤더에 대한 값이 잘못된 GraphQL 쿼리 아래에서 실행합니다.

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u>예상 결과</u>:

오류 메시지: &quot;요청한 스토어를 찾을 수 없습니다. 스토어를 확인하고 다시 시도하십시오.&quot;

<u>실제 결과</u>:

다음과 같은 치명적인 오류:

```Allowed memory size of 792723456 bytes exhausted```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
