---
title: 'ACSD-55352: 보상 포인트를 사용하여 대변 메모 생성'
description: ACSD-55352 패치를 적용하여 고객 보상 포인트가 포함된 부분 대변 메모를 만든 후 주문 상태가 *마감됨*으로 변경되고 관리자 주문 페이지에서 대변 메모 옵션이 사라지는 Adobe Commerce 문제를 해결합니다.
feature: Checkout, Orders
role: Admin, Developer
exl-id: bee0c4be-11ec-4dcb-9b3c-7af26676cee9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-55352: 보상 포인트를 사용하여 대변 메모 생성

ACSD-55352 패치는 고객 보상 포인트가 포함된 부분 대변 메모를 만든 후 주문 상태가 *마감됨*(으)로 변경되고 대변 메모 옵션이 관리자 주문 페이지에서 사라지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-55352입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 보상 포인트가 포함된 부분 크레딧 메모를 만든 후 주문 상태가 *마감됨*(으)로 변경되고 크레딧 메모 옵션이 관리자 주문 페이지에서 사라집니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자에 로그인합니다.
2. **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**(으)로 이동합니다.
3. 두 개의 요금을 추가합니다.
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *통화 포인트*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *포인트 통화*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. 가격이 *$100*&#x200B;이고 수량이 *수량*: *100*&#x200B;인 간단한 제품을 만드십시오.
5. 상점에서 고객을 만듭니다.
6. 백엔드로 다시 이동 : **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > *100*&#x200B;을(를) 추가하고 고객을 저장합니다.
7. 상점으로 이동한 다음 고객이 이전에 만든 것으로 로그인합니다.
8. *수량*: *10*&#x200B;인 장바구니에 제품을 추가합니다.
9. **[!UICONTROL Checkout]**(으)로 이동하여 메시지가 표시되면 사용 가능한 *100* 보상 포인트를 사용하고 주문을 하십시오.
10. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]**(으)로 이동하여 해당 주문을 배송합니다.
11. [!UICONTROL Credit Memo]&#x200B;(으)로 이동하여 *환불할 수량*&#x200B;을(를) *8*(으)로 업데이트하십시오.
12. **[!UICONTROL Refund Reward Points]** 확인란을 선택하고 **[!UICONTROL Refund offline]**&#x200B;을(를) 클릭합니다.
13. [!UICONTROL Credit Memo]을(를) 사용하여 주문에서 나머지 두 제품을 환불해 보십시오.

<u>예상 결과</u>:

* 관리자가 [!UICONTROL Credit Memo]을(를) 만들어 나머지 두 제품을 반환합니다.
* 주문 상태는 *완료*&#x200B;입니다.

<u>실제 결과</u>:

* [!UICONTROL Credit Memo]을(를) 더 만들 수 없습니다.
* 주문 상태는 *마감됨*&#x200B;입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
