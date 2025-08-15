---
title: 'ACSD-61133: ''sales_clean_quotes'' cron 이 승인되지 않은 구매 발주에서 견적을 삭제합니다.'
description: ACSD-61133 패치를 적용하여 'sales_clean_quotes' cron 이 승인되지 않은 구매 발주에서 견적을 삭제하는 Adobe Commerce 문제를 수정합니다.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133: `sales_clean_quotes` 크론은 승인되지 않은 구매 주문에서 견적을 삭제합니다.

ACSD-61133 패치는 `sales_clean_quotes` 크론이 승인되지 않은 구매 주문에서 견적을 삭제하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61133입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 및 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`sales_clean_quotes` cron이 승인되지 않은 구매 주문에서 견적을 삭제합니다. 크론이 구매된 주문을 삭제하므로 *[B2B 구매 주문]*&#x200B;을(를) 구매된 주문과 연결된 견적의 주문으로 변환할 수 없습니다.

<u>필수 구성 요소</u>:

Adobe Commerce [!UICONTROL B2B] 모듈이 설치되고 사용하도록 설정되었습니다.

<u>재현 단계</u>:

1. *[!UICONTROL B2B Purchase Order]* 기능을 사용하도록 설정합니다.
1. 회사를 만듭니다.
1. *[!UICONTROL Purchase Order]* 만들기
1. 견적이 만료되고 cron에 의해 삭제될 때까지 기다립니다. 견적 만료 기간은 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**(으)로 설정할 수 있습니다.
1. *[!UICONTROL Purchase Order]* 또는 *[!UICONTROL My Purchase Order in Customer Dashboard]* [!DNL GraphQL] 돌연변이를 통해 `placeOrderForPurchaseOrder`을(를) 순서로 전환합니다.

<u>예상 결과</u>:

활성 *[!UICONTROL Purchase Order]*&#x200B;과(와) 연결된 견적이 크론에 의해 만료되어 삭제되지 않았습니다. 주문은 상점 또는 [!DNL GraphQL]을(를) 통해 성공적으로 완료되었습니다.

<u>실제 결과</u>:

주문이 실행되지 않고 상점 앞에 오류가 표시되거나 [!DNL GraphQL] 응답에서 오류가 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
