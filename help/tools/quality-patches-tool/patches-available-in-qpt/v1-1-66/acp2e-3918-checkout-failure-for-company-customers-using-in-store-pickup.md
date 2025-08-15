---
title: 'ACP2E-3918: 매장 내 픽업을 사용하는 회사 고객의 체크아웃 실패'
description: ACP2E-3918 패치를 적용하여 기본 청구 주소 없이 매장 픽업을 사용하여 로그인한 회사 고객에 대한 체크아웃이 실패하는 Adobe Commerce 문제를 수정합니다.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACP2E-3918: 매장 내 픽업을 사용하는 회사 고객의 체크아웃 실패

ACP2E-3918 패치는 기본 청구 주소 없이 매장 픽업을 사용하여 로그인한 회사 고객을 체크아웃하지 못하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3918입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기본 주소가 없는 로그인한 회사 고객이 매장 픽업을 사용하여 구매 발주를 시도하면 체크아웃이 실패합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Purchase Orders]** 사용
1. **[!UICONTROL Company]**&#x200B;을(를) 만들고 **[!UICONTROL Purchase Orders]**&#x200B;을(를) 사용하도록 설정합니다.
1. 저장된 주소 없이 **[!UICONTROL Company User]**&#x200B;을(를) 만듭니다.
1. **[!UICONTROL In-Store Delivery]** 배송 방법을 사용하도록 설정합니다.
1. 인벤토리 소스를 추가합니다.
1. 재고 재고를 추가합니다.
1. 제품에 재고를 지정합니다.
1. 프론트엔드에서 회사 사용자로 로그인합니다.
1. 제품을 **[!UICONTROL Cart]**&#x200B;에 추가합니다.
1. 체크아웃을 진행합니다.
1. 배송 단계에서 **[!UICONTROL In-Store Pick Up]**&#x200B;을(를) 선택하십시오.
1. 결제를 진행합니다.

<u>예상 결과</u>:

결제 단계는 체크아웃 중에 로드되어야 하며 브라우저 콘솔에 오류가 표시되지 않아야 합니다.

<u>실제 결과</u>:

결제 단계가 로드되지 않고 브라우저 콘솔에 다음 JavaScript 오류가 표시됩니다.

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
