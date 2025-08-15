---
title: 'MDVA-44100: 장바구니에 있는 마지막 제품에 모든 FPT가 할당됨'
description: MDVA-44100 패치는 모든 FPT가 장바구니의 마지막 제품에 할당되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44100입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: b370dcbb-cbe9-4f5d-9b8f-1722ab521fcb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-44100: 장바구니에 있는 마지막 제품에 모든 FPT가 할당됨

MDVA-44100 패치는 모든 FPT가 장바구니의 마지막 제품에 할당되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44100입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

모든 FPT는 장바구니에 있는 마지막 제품에 할당되고 나머지 제품에 대한 FPT 값이 재설정됩니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **판매** > **세금**(으)로 이동하여 다음을 설정합니다.
   * FPT 활성화 = 예
   * FPT에 세금 적용 = 예
   * 소계에 FPT 포함 = 예
1. **스토어** > **특성** > **제품**(으)로 이동하여 유형 = 고정 제품 세금으로 새 특성을 만드십시오.
1. 속성 집합에 속성을 추가합니다.
1. 속성 세트에서 두 제품을 만들고 국가 및 주에 대한 FPT 속성을 구성합니다.
1. 두 항목을 모두 주문에 추가합니다.
1. FPT를 지불해야 하는 주소를 입력합니다.
1. 주문하십시오.
1. 주문의 항목 목록을 확인하십시오.

<u>예상 결과</u>:

각 제품 아래에 FPT가 표시됩니다.

<u>실제 결과</u>:

두 항목의 FPT 값이 두 번째 항목 아래에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
