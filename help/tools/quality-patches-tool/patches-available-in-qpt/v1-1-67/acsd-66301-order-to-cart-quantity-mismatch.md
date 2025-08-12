---
title: 'ACSD-66301: Commerce 관리자의 주문에서 장바구니로 제품을 이동하면 수량이 일치하지 않습니다'
description: ACSD-66301 패치를 적용하여 관리 패널에서 주문을 만들 때 고객 장바구니에 있는 제품이 주문에 추가된 후 제거되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9a4224c02634514a9428dc6b0daf4c1d5f5c7c43
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-66301: 주문에서 Commerce 관리자의 장바구니로 제품을 다시 이동하면 수량이 일치하지 않습니다

ACSD-66301 패치는 주문에서 관리자의 장바구니로 제품을 다시 이동하면 수량이 일치하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66301입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p10, 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문에서 Commerce 관리자의 장바구니로 제품을 다시 이동하면 수량이 일치하지 않습니다.

<u>재현 단계</u>:

1. 상점 전면을 통해 사용자를 만듭니다.
2. 수량 = *5*&#x200B;인 장바구니에 제품을 추가합니다.
3. 관리 패널로 이동하여 제품이 추가된 사용자 계정을 엽니다.
4. **[!UICONTROL Create Order]**&#x200B;을(를) 클릭합니다.
5. 왼쪽 패널에서 추가된 제품 및 수량을 포함한 고객의 활동을 볼 수 있습니다.
6. 주문에 제품을 추가합니다.
7. 주 주문 섹션에서 수량 = *4*&#x200B;을(를) 업데이트합니다.
8. **[!UICONTROL Update Items and Quantities]** 단추를 클릭합니다.
9. 선택한 품목을 주문에서 고객의 장바구니로 다시 전송합니다.

<u>예상 결과</u>:

새 수량 = *4*(으)로 장바구니에 제품이 추가되었습니다.

<u>실제 결과</u>:

제품이 장바구니에 추가되었습니다. 이전 수량 = *5*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
