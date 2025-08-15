---
title: 'ACSD-65913: [!DNL OpenSearch] 가격이 같은 제품의 범주에 대해 illegal_argument_exception을 throw합니다.'
description: ACSD-65913 패치를 적용하여  [!DNL Opensearch] 이(가) 같은 가격의 모든 제품을 포함하는 범주에 illegal_argument_exception("[from] 매개 변수는 음수일 수 없음")을 발생시키는 Adobe Commerce 문제를 해결합니다.
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: e24b62305ef97c5fff13582b4bb68f622dffb6d3
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-65913: [!DNL OpenSearch]은(는) 가격이 같은 제품의 범주에 대해 `illegal_argument_exception`을(를) throw합니다.

ACSD-65913 패치를 사용하면 [!DNL OpenSearch]에서 가격이 같은 제품에 대해 `illegal_argument_exception`을(를) 발생시키는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65913입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL OpenSearch]은(는) 모든 제품이 동일한 가격을 공유하는 범주를 로드할 때 `illegal_argument_exception`(*[from] 매개 변수는 음수일 수 없음*)을(를) throw합니다.

<u>재현 단계</u>:

1. [!DNL OpenSearch] 버전 2.19.1을 설치하고 기본 검색 엔진으로 설정합니다.
1. 계층화된 탐색에 표시되도록 **[!UICONTROL Price]** 제품 특성을 구성합니다.
   1. **[!UICONTROL Visible in Advanced Search]**: *예*
   1. **[!UICONTROL Comparable on Storefront]**: *예*
   1. **[!UICONTROL Use in Layered Navigation]**: *필터링 가능(결과 포함)*
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**(으)로 이동합니다. **[!UICONTROL Price Navigation Step Calculation]**&#x200B;을(를) *자동(제품 개수 균등화)*(으)로 설정합니다.
1. 가격이 모두 동일한 6개의 제품으로 카테고리를 만듭니다.
   1. SKU: product_super_0-1-1-1, 가격: $150
   1. SKU: product_super_0-1-1, 가격: $48
   1. SKU: product_super_0-1, 가격: $48
   1. SKU: product_super_0, 가격: $48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1, 가격: $48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1, 가격: $48
1. 다음 명령을 실행합니다.
   `bin/magento indexer:reindex`
1. 카테고리 페이지를 엽니다. 다음 오류가 표시됩니다.
   *[from] 매개 변수는 음수일 수 없습니다. [-1]*&#x200B;을(를) 찾았습니다.

<u>예상 결과</u>:

범주의 모든 제품에 같은 가격이 있을 때 [!DNL OpenSearch]에서 `illegal_argument_exception`을(를) throw하면 안 됩니다.

<u>실제 결과</u>:

* [!DNL OpenSearch]이(가) 메시지와 함께 `illegal_argument_exception`을(를) 발생시킵니다.
  *[from] 매개 변수는 음수일 수 없습니다. [-1]*&#x200B;을(를) 찾았습니다.

* `var/log/exception.log` 파일에는 다음이 포함되어 있습니다.

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
