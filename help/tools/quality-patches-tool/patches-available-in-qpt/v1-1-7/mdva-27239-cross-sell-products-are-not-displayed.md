---
title: 'MDVA-27239: 크로스셀 제품이 표시되지 않음'
description: MDVA-27239 패치는 크로스셀 제품이 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239: 크로스셀 제품이 표시되지 않음

MDVA-27239 패치는 크로스셀 제품이 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.3.4, 2.4.0

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니 페이지의 교차 판매 블록에는 교차 판매 제품이 표시되지 않습니다.

<u>필수 구성 요소</u>:

1. Magento_TargetRule 모듈을 비활성화하거나 레이아웃 블록 Magento\TargetRule\Block\Checkout\Cart\Crosssell에서 제거합니다.
1. 제품 1 만들기.
1. 제품 1에 대한 일정 업데이트를 만들어 새로 만든 제품의 row_id가 entity_id와 다릅니다.
1. 제품 2, 제품 3 및 제품 4를 만듭니다.
1. 제품 3을 제품 4에 대한 교차 판매로 설정합니다.
1. 제품 4를 제품 2에 대한 교차 판매로 설정합니다.

<u>재현 단계</u>:

1. 제품 4 및 제품 2를 장바구니에 추가합니다.
1. 장바구니 페이지를 확인합니다.

<u>예상 결과</u>:

제품 3은 크로스셀 블록에 표시됩니다.

<u>실제 결과</u>:

크로스셀 블록이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
