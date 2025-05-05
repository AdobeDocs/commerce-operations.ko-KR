---
title: 'ACSD-63992: 관리 UI에 쿠폰 및 배송 방법 상태 오류가 있는 [!UICONTROL Cart Price Rule]'
description: ACSD-63992 패치를 적용하여 쿠폰이 포함된 [!UICONTROL Cart Price Rule]과(와) 배송 방법에 따른 조건이 관리 UI를 통해 올바르게 적용되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Price Rules, Admin Workspace
role: Admin, Developer
source-git-commit: ef17f2f75eae16e3efada4ea08ee0f068fd60702
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-63992: 관리 UI에 쿠폰 및 배송 방법 상태 오류가 있는 [!UICONTROL Cart Price Rule]

ACSD-63992 패치는 배송 방법에 따라 쿠폰과 조건이 있는 [!UICONTROL Cart Price Rule]이(가) 관리 UI를 통해 올바르게 적용되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63992입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니 규칙에 **[!UICONTROL Conditions]** 섹션 내의 배송 방법에 대한 조건이 포함된 경우 관리 패널을 통해 주문을 만들 때 관련 쿠폰 코드가 적용되지 않습니다. 대신 시스템에 다음 오류가 표시됩니다.

_&lt;> 쿠폰 코드가 잘못되었습니다. 코드를 확인하고 다시 시도하십시오._

<u>재현 단계</u>:

1. 장바구니 가격 규칙을 만들고 조건을 설명합니다.
   * *[!UICONTROL Conditions]*&#x200B;에서: 배송 방법을 포함하는 조건을 추가합니다(예: *[!UICONTROL Flat Rate]*).
   * *[!UICONTROL Rule Information]*&#x200B;에서: **[!UICONTROL Coupon]**&#x200B;을(를) *[!UICONTROL Specific Coupon]*(으)로 설정한 다음 **[!UICONTROL Coupon Code]**&#x200B;을(를) *TEST*(으)로 입력합니다.
1. 관리 패널에서 새 주문을 만들고 **[!UICONTROL Apply Coupon]** 필드에 쿠폰 코드 *TEST*&#x200B;을(를) 입력합니다.

<u>예상 결과</u>:

쿠폰이 정상적으로 적용되었습니다.

<u>실제 결과</u>:

다음 오류 메시지가 나타납니다.

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
