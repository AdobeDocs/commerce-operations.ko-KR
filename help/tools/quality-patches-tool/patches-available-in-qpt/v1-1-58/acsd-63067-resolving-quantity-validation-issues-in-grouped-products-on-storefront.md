---
title: 'ACSD-63067: 상점 첫 화면의 그룹화된 제품에서 수량 검증 문제 해결'
description: ACSD-63067 패치를 적용하여 한 제품에만 부정확한 수량이 있는 경우 그룹화된 제품의 모든 제품 수량이 부적합한 것으로 잘못 강조 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Storefront
role: Admin, Developer
exl-id: a497f2c4-8bf0-41da-955a-a58e79f09c08
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067: 상점 첫 화면의 그룹화된 제품에서 수량 검증 문제 해결

ACSD-63067 패치는 한 제품에만 부정확한 수량이 있을 때 그룹화된 제품의 모든 제품 수량이 부적합한 것으로 잘못 강조 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63067입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

그룹화된 제품에서 하위 제품 중 하나에 유효하지 않은 수량이 있으면 모든 수량이 유효하지 않은 것으로 잘못 강조 표시됩니다. 또한 수량이 잘못된 제품에 대해서만 유효성 검사 메시지가 표시되는 대신 모든 제품에 대해 유효성 검사 메시지가 나타납니다.

<u>재현 단계</u>:

1. 두 개 이상의 간단한 제품을 옵션으로 사용하여 그룹화된 새 제품을 만듭니다.
1. 상점에서 제품을 개봉하세요.
1. 옵션 중 하나에 유효하지 않은 수량(예: -1)을 입력하고 나머지 옵션에 유효한 수량(예: 1)을 입력합니다.
1. **[!UICONTROL Add to Cart]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

수량이 잘못된 제품만 부적합으로 강조 표시됩니다.

<u>실제 결과</u>:

모든 제품 수량이 잘못된 것으로 강조 표시되어 있고 *제품의 수량을 지정하십시오. 모든 제품*&#x200B;에 대해 표시됩니다.


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
