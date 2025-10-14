---
title: 'MDVA-44562: 기본 스토어 ID로 재정의된 견적 항목의 스토어 ID'
description: MDVA-44562 패치는 기본 스토어 ID가 GraphQL 요청에 대한 견적 항목에 대한 스토어 ID를 무시하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44562입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562: 기본 스토어 ID로 재정의된 견적 항목의 스토어 ID

MDVA-44562 패치는 기본 스토어 ID가 GraphQL 요청에 대한 견적 항목에 대한 스토어 ID를 무시하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44562입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

견적 항목의 스토어 ID가 GraphQL 요청의 기본 스토어 ID로 재정의됩니다.

<u>재현 단계</u>:

1. 새 스토어 뷰를 만듭니다.
1. 스토어 보기당 이름이 다른 간단한 새 제품을 만듭니다.
1. 새 고객을 만듭니다.
1. 고객 인증 토큰을 얻습니다.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. 인증 토큰을 사용하여 고객에 대한 새 견적을 만듭니다.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. 장바구니에 제품을 추가합니다.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. 기본 스토어 보기에 대한 장바구니 콘텐츠를 가져옵니다.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. 새 스토어 보기에 대한 장바구니 콘텐츠를 가져옵니다.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>예상 결과</u>:

새 스토어 보기의 응답은 새 스토어 보기의 제품 이름을 표시합니다.

<u>실제 결과</u>:

새 스토어 보기의 응답은 기본 스토어 보기 아래에 제품 이름 설정을 표시합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서 &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
