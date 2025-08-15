---
title: 'MDVA-42969: 관련 제품 규칙은 고객 세그먼트가 모두로 설정된 경우에만 작동합니다'
description: MDVA-42969 패치는 고객 세그먼트가 모두로 설정된 경우에만 관련 제품 규칙이 작동하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42969입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969: 관련 제품 규칙은 고객 세그먼트가 모두로 설정된 경우에만 작동합니다

MDVA-42969 패치는 고객 세그먼트가 모두로 설정된 경우에만 관련 제품 규칙이 작동하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42969입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관련 제품 규칙은 고객 세그먼트가 모두로 설정된 경우에만 작동합니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **카탈로그** > **규칙 기반 제품 관계**(으)로 이동하여 **관련 제품 표시** = **규칙 기반 전용**&#x200B;을 설정합니다.
1. **고객** > **세그먼트**(으)로 이동하여 새 세그먼트를 만듭니다. **적용 대상** = **방문자 및 등록된 고객**.
1. **마케팅** > **관련 제품 규칙**(으)로 이동하여 새 규칙을 만듭니다.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. 상점 첫 화면에서 일치하는 제품을 열고 표시할 제품이 표시되는지 확인합니다.
1. 3단계에서 만든 규칙을 수정하고 2단계에서 **고객 세그먼트** = **특정** > **세그먼트**&#x200B;를 설정합니다.
1. 상점에서 일치하는 상품을 엽니다.

<u>예상 결과</u>:

고객 세그먼트는 다음 구성으로 생성되기 때문에 규칙 기반 관련 제품은 제품 방문자를 위한 상점 첫 화면에 표시됩니다.

**적용 대상** = **방문자 및 등록된 고객**

<u>실제 결과</u>:

관련 제품이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
