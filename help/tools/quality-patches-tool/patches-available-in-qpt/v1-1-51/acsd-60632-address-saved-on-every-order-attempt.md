---
title: 'ACSD-60632: 모든 주문 시도와 함께 저장된 주소'
description: ACSD-60632 패치를 적용하여 주문이 성공적으로 생성되었는지 여부에 관계없이 각 주문 배치 시도와 함께 새 주소가 저장되는 Adobe Commerce 문제를 수정합니다.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: 모든 주문 시도와 함께 저장된 주소

ACSD-60632 패치는 주문이 성공적으로 생성되었는지 여부에 관계없이 각 주문 배치 시도에 따라 새 주소가 저장되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-60632입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 배치가 시도될 때마다 주문이 성공적으로 생성되었는지 여부에 관계없이 새 주소 항목이 시스템에 저장됩니다.

<u>재현 단계</u>:

1. **[!DNL PayPal Payflow Link]** 결제 방법 사용:
   * 로컬 컴퓨터에서 시스템이 실제 IP 없이 [!DNL PayPal Payflow Link]에서 API 호출을 받을 수 없습니다.
1. 간단한 제품을 만듭니다.
1. 주소 없이 등록된 고객을 만듭니다.
1. 제품을 장바구니에 추가합니다.
1. 체크아웃을 진행합니다.
1. 주소를 입력하십시오. 이 단계에서 첫 번째 주소가 생성되었는지 확인합니다.
1. *[!UICONTROL Review and Payments]* 페이지에서 **[!UICONTROL Credit Card (Payflow Link)]** 라디오 단추를 선택합니다.
1. **[!UICONTROL Continue]** 클릭:
   * 체크아웃 페이지는 미리 채워진 주소와 예상 오류 메시지가 있는 *[!UICONTROL Review and Payments]* 단계로 돌아갑니다.
1. *[!UICONTROL Credit Card (Payflow Link)]* 라디오 단추를 다시 선택하십시오.
1. **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

두 번째 주문 배치 시도에서는 새 주소가 만들어지지 않습니다.

<u>실제 결과</u>:

모든 주문 배치 시도 후에 새 주소가 만들어집니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
