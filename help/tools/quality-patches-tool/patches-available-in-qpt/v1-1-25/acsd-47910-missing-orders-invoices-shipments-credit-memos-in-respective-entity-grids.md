---
title: 'ACSD-47910: 각 개체 그리드에 주문, 송장, 선적, 대변 메모 누락'
description: ACSD-47910 패치를 적용하여 각 엔티티 그리드에 누락된 주문, 송장, 선적 및 대변 메모가 있는 Adobe Commerce 문제를 수정합니다.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910: 각 개체 그리드에 주문, 송장, 선적 및 대변 메모 누락

ACSD-47910 패치는 각 개체 그리드에 누락된 주문, 송장, 선적 및 대변 메모가 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47910입니다. 이 문제가 수정되는 버전은 아직 사용할 수 없습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.4-p1

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

각 개체 그리드에 누락된 주문, 송장, 선적 및 대변 메모.

<u>재현 단계</u>:

1. **[!UICONTROL Asynchronous indexing]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]**&#x200B;에서 **[!UICONTROL Grid Settings]**&#x200B;을(를) 사용하도록 설정합니다.
1. 두 가지를 주문하십시오.
1. cron을 실행하여 해당 주문을 그리드에 동기화합니다.
1. 주문 중 하나를 열고 송장을 발행할 준비를 하십시오. 아직 송장을 제출하지 마십시오.
1. 프론트엔드에 배치하기 위해 새로운 주문을 준비합니다. 아직 주문 버튼을 클릭하지 마십시오.
1. `sleep(30)`의 `foreach`에 `NotSyncedDataProvider::L43`을(를) 추가합니다.
1. `bin/magento cron:run` 실행.
1. 이제 새로운 주문을 합니다.
1. 이전 주문에 대한 송장을 발행합니다.
1. 새 주문이 동기화되어야 하므로 cron 을 다시 실행하십시오.
1. 관리자의 주문 그리드로 이동합니다.

<u>예상 결과</u>:

주문 그리드에 새 주문이 표시됩니다.

<u>실제 결과</u>:

이전 주문 업데이트가 표(**[!UICONTROL status: Processing]**)에 동기화되었습니다. 새 순서는 격자에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
