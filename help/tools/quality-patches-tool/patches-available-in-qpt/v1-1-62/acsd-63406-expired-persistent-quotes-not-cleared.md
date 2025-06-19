---
title: 'ACSD-63406: persistent_clear_expired cron 작업이 실행될 때 만료된 영구 견적이 지워지지 않음'
description: ACSD-63406 패치를 적용하여 'persistent_clear_expired' cron 작업이 실행될 때 cron 작업에서 만료된 지속 견적이 지워지지 않는 Adobe Commerce 문제를 해결합니다.
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-63406: `persistent_clear_expired` cron 작업이 실행될 때 만료된 영구 따옴표가 지워지지 않습니다.

ACSD-63406 패치는 `persistent_clear_expired` cron 작업이 실행될 때 cron 작업에서 만료된 영구 따옴표가 지워지지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-63406입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`persistent_clear_expired` cron 작업이 실행될 때 cron 작업에서 만료된 영구 견적이 지워지지 않습니다.

<u>재현 단계</u>:

1. 카테고리 및 제품을 만듭니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**(으)로 이동합니다.
   1. 모든 옵션을 *예*(으)로 설정합니다.
   1. **[!UICONTROL Persistence Lifetime (seconds)]**&#x200B;을(를) *60*(으)로 설정합니다.
1. 상점 첫 화면에서 고객 계정을 만들고 로그인합니다.
1. 장바구니에 제품을 추가합니다.
1. 로그아웃한 후 60초 동안 기다린 후 다시 로그인합니다.

<u>예상 결과</u>:

`persistent_clear_expired` cron 작업은 구성의 지속성 수명 설정을 기반으로 지속성 따옴표를 삭제해야 합니다.

<u>실제 결과</u>:

고객 견적의 `is_persistent` 값은 견적 테이블에 *1* 상태로 남아 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
