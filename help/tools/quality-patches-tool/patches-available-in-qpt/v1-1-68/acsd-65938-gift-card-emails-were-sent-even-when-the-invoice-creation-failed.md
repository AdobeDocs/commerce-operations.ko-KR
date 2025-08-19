---
title: 'ACSD-65938: 송장 생성에 실패했을 때도 기프트 카드 이메일이 전송됨'
description: ACSD-65938 패치를 적용하여 송장이 성공적으로 저장되고 커밋되기 전에 기프트 카드 이메일이 전송된 Adobe Commerce 문제를 수정하여 송장이 제대로 저장된 후에 이메일이 트리거되도록 합니다.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938: 송장 생성에 실패했을 때도 기프트 카드 이메일이 전송됨

ACSD-65938 패치는 송장이 정상적으로 저장되고 커밋되기 전에 기프트 카드 이메일이 전송되던 문제를 해결합니다. 이 수정 사항으로 이제 송장이 성공적으로 저장된 후에만 이메일이 트리거됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65938입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기프트 카드 이메일은 송장이 정상적으로 생성 및 저장되었는지 확인하기 전에 전송되었으므로 송장 생성에 실패한 경우에도 이메일이 전송됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** 패널에 로그인합니다.
2. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]**(으)로 이동한 다음 **[!UICONTROL Generate Gift Card Account when Order Item is]**&#x200B;을(를) *인보이스 발행*(으)로 설정합니다.
3. 새 기프트 카드 제품을 만듭니다.
4. 장바구니에 선물 장바구니 제품을 추가하고 **[!UICONTROL checkout]**(으)로 진행합니다. **[!UICONTROL Check/Money Order]**&#x200B;을(를) 결제 방법으로 사용할 수 있습니다.
5. 주문하십시오.
6. 주문 배치 중에 예외를 시뮬레이션하도록 `OrderRepository`을(를) 수정하십시오.
7. 다음 페이로드를 사용하여 `rest/default/V1/order/<ORDER_ID>/invoice`에게 POST 요청을 보냅니다.

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u>예상 결과</u>:

송장 작성이 실패할 경우 기프트 카드 이메일을 보내지 않습니다.

<u>실제 결과</u>:

송장 작성이 실패했는데도 기프트 카드 이메일이 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
