---
title: 'ACSD-64209: Cron 스케줄러는 [!UICONTROL Ordered]개의 견적을 제외하지 않고 협상가능한 견적을 검색합니다.'
description: ACSD-64209 패치를 적용하여 cron 스케줄러가 상태가 [!UICONTROL Ordered]인 견적을 제외하지 않고 모든 협상 가능한 견적을 검색하므로 전자 메일 또는 전자 메일이 트리거되는 Adobe Commerce 문제를 해결합니다.
feature:  B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: Cron 스케줄러는 [!UICONTROL Ordered]개의 견적을 제외하지 않고 협상가능한 견적을 검색합니다.

ACSD-64209 패치는 cron 스케줄러가 상태가 **[!UICONTROL Ordered]**&#x200B;인 견적을 제외하지 않고 모든 협상 가능한 견적을 검색하므로 전자 메일 또는 전자 메일이 트리거되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64209입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

cron 스케줄러는 상태가 **[!UICONTROL Ordered]**&#x200B;인 견적을 제외하지 않고 모든 협상 가능한 견적을 검색하므로 전자 메일 또는 전자 메일이 트리거됩니다.

<u>재현 단계</u>:


1. *관리자* 사이드바에서 **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**(으)로 이동하여 회사 및 B2B 견적을 사용하도록 설정합니다.
1. *관리자* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**&#x200B;에서 **[!UICONTROL Default Expiration Period]**&#x200B;을(를) *1*(으)로 설정합니다.
1. 회사를 만들고 활성화한 다음 회사 관리자로 로그인합니다.
1. 장바구니에 제품을 추가합니다.
1. 견적을 요청합니다.
1. *관리자* 사이드바에서 **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**(으)로 이동합니다.
1. 생성된 견적을 선택하고 **[!UICONTROL Send]**&#x200B;을(를) 클릭하여 구매자에게 견적을 다시 보냅니다.
1. 상점 첫 화면에서 회사 관리자로 로그인합니다.
1. 견적을 선택하고 **[!UICONTROL Proceed to checkout]**&#x200B;을(를) 클릭하여 구매를 완료합니다.
1. 견적의 상태가 **[!UICONTROL Ordered]**&#x200B;이고 더 이상 상점 앞에서 작업을 수행할 수 없는지 확인하세요.
1. `negotiable_quote_send_emails` cron 작업을 트리거합니다.


<u>예상 결과</u>:

견적이 주문되었으며 더 이상 조치를 취할 수 없으므로 견적 만료에 대한 이메일이 전송되지 않아야 합니다.

<u>실제 결과</u>:

전자 메일 *견적이 곧 만료됩니다*&#x200B;이(가) 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
