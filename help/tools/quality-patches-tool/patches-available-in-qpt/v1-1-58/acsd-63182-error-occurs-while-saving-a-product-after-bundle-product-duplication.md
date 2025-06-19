---
title: 'ACSD-63182: 번들 제품 복제 후 제품을 저장하는 도중 오류 발생'
description: ACSD-63182 패치를 적용하여 번들 제품이 MSI가 활성화된 상태로 복제된 후 제품을 저장하는 동안 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182: 번들 제품 복제 후 제품을 저장하는 도중 오류 발생

ACSD-63182 패치는 번들 제품 복제 후 번들 옵션으로 사용되는 간단한 제품을 저장할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63182입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

번들 제품을 복제한 후 번들 옵션으로 사용되는 간단한 제품을 저장할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. 새 MSI 소스 및 스톡을 만듭니다.
1. 두 개의 간단한 제품을 만듭니다. **p1** 및 **p2**.
1. 번들 옵션으로 **p1** 및 **p2**&#x200B;이(가) 있는 번들 제품 **b1**&#x200B;을(를) 만듭니다.
1. **번들 제품 b1**&#x200B;을(를) 편집하고 ***[!UICONTROL Save and Duplicate]***&#x200B;을(를) 클릭합니다.
1. **단순 제품 p1**&#x200B;을(를) 편집하고 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

제품이 오류 없이 저장됩니다.

<u>실제 결과</u>:

다음 오류가 표시됩니다.
*예외: ID가 &#39;XXX&#39;인 항목(Magento\Catalog\Model\Product\Interceptor)이 이미 있습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
