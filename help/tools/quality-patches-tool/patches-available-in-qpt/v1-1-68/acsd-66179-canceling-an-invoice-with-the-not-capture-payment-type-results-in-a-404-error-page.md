---
title: 'ACSD-66179: 결제 유형이 [!UICONTROL Not Capture]인 송장을 취소하면 404 오류 페이지가 표시됩니다.'
description: ACSD-66179 패치를 적용하여 [!UICONTROL Not Capture] 결제 유형의 송장을 취소하면 404 오류 페이지가 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-66179: 결제 유형이 [!UICONTROL Not Capture]인 송장을 취소하면 404 오류 페이지가 표시됩니다.

ACSD-66179 패치는 *[!UICONTROL Not Capture]* 결제 유형으로 만든 송장을 취소하면 404 오류 페이지가 표시되는 문제를 해결했습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66179입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Not Capture]* 결제 유형으로 만든 송장을 취소하면 404 오류 페이지가 표시됩니다.

<u>재현 단계</u>:

1. PayPal Express Checkout과 같은 결제 방법을 사용하여 주문을 만듭니다.
1. 송장을 생성합니다. **[!UICONTROL Amount]**&#x200B;을(를) *[!UICONTROL Not Capture]*(으)로 설정하고 송장을 제출합니다.
1. 생성된 송장을 열고 **[!UICONTROL Cancel]**&#x200B;을(를) 선택합니다.

<u>예상 결과</u>:

1. 송장이 정상적으로 취소되었습니다.
1. 성공 메시지가 표시됩니다. *송장을 취소했습니다.*

<u>실제 결과</u>:

404 오류 페이지가 표시됩니다. *페이지를 찾을 수 없습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
