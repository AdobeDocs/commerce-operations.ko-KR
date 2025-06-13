---
title: 'MDVA-40961: 항목의 최소 수량이 이미 장바구니에 있는 경우 항목을 장바구니에 추가할 수 없습니다.'
description: MDVA-40961 패치는 항목의 최소 수량이 장바구니에 이미 있는 경우 장바구니에 추가 항목을 추가할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40961입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Orders, Shopping Cart
role: Admin
exl-id: b5191919-062d-4ddd-84e2-a4801501724d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-40961: 항목의 최소 수량이 이미 장바구니에 있는 경우 항목을 장바구니에 추가할 수 없습니다.

MDVA-40961 패치는 항목의 최소 수량이 장바구니에 이미 있는 경우 장바구니에 추가 항목을 추가할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40961입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

항목의 최소 수량이 이미 장바구니에 있는 경우 장바구니에 추가 항목을 추가할 수 없습니다.

<u>재현 단계</u>:

1. 단순 제품을 장바구니에서 둘 이상의 **최소 허용 수량**(예: 두 개)으로 설정합니다.
1. 상점에서 제품을 열고 두 개를 장바구니에 추가합니다.
1. 제품 페이지를 벗어나지 말고 장바구니에 이 제품 중 하나를 더 추가하십시오.

<u>예상 결과</u>:

세 번째 제품은 이미 최소 수량을 포함하고 있으므로 장바구니에 추가할 수 있습니다.

<u>실제 결과</u>:

다음 오류 메시지가 표시됩니다. *구매할 수 있는 최소 수량은 2*&#x200B;입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
