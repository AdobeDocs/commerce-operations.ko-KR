---
title: 'ACSD-45754: 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않음'
description: ACSD-45754 패치는 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45754입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-45754: 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않음

ACSD-45754 패치는 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45754입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.5

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 쿠폰 적용 후 보상 포인트는 추가되지 않습니다.

<u>필수 구성 요소</u>:

PayPal 결제 방법이 구성되어 있습니다.

<u>재현 단계</u>:

1. **스토어** > **기타 설정** > **보상 환율**&#x200B;로 이동하여 보상 포인트 환율을 만드십시오.
1. 쿠폰 코드가 있는 장바구니 가격 규칙을 만들어 로그인한 고객에 대해 100개의 보상 포인트를 적용합니다.
1. PayPal과 쿠폰 코드를 사용하여 로그인한 고객으로 제품을 확인하십시오.
1. 관리자의 고객 계정에서 보상 포인트 내역을 확인합니다.

<u>예상 결과</u>:

가격 규칙에 따라 고객에게 보상 포인트가 추가됩니다.

<u>실제 결과</u>:

고객에게 보상 포인트가 추가되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서 &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
