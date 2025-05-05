---
title: 'ACSD-58685: 재활성화 시 비활성화된 판매 이메일이 전송됩니다.'
description: ACSD-58685 패치를 적용하여 이메일 통신이 비활성화되는 동안 시작된 판매 이메일이 이메일 통신이 다시 활성화되면 전송되는 Adobe Commerce 문제를 해결합니다.
feature: Configuration
role: Admin, Developer
source-git-commit: db495f2dbf307f9da42b6dc4fc7bed1e6af1d307
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685: 재활성화 시 비활성화된 판매 이메일이 전송됩니다.

ACSD-58685 패치는 이메일 통신이 비활성화되어 있는 동안 시작된 판매 이메일이 이메일 통신이 다시 활성화되면 전송되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-58685입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이메일 커뮤니케이션이 비활성화된 상태에서 시작된 판매 이메일은 이메일 커뮤니케이션이 다시 활성화되면 전송됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]**(으)로 이동한 다음 **[!UICONTROL Disable Email Communications]**&#x200B;을(를) *[!UICONTROL No]*(으)로 설정합니다.
1. **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]**(으)로 이동하고 **[!UICONTROL Asynchronous Sending]**&#x200B;을(를) *[!UICONTROL Yes]*(으)로 설정합니다.
1. 구성 캐시를 지웁니다.
1. 주문하십시오.
1. 이메일 통신을 활성화합니다.
1. 다른 주문을 하십시오.
1. 크론을 작동시키세요

<u>예상 결과</u>:

두 번째 주문에 대한 이메일만 발송됩니다.

<u>실제 결과</u>:

첫 번째 주문과 두 번째 주문 모두에 대한 이메일이 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
