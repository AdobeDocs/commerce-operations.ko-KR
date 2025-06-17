---
title: 'ACSD-65202: 내 계정 페이지에 다른 스토어 보기의 최근 주문이 표시되지 않습니다'
description: ACSD-65202 패치를 적용하여 [내 계정] 페이지에 동일한 스토어 내 다른 스토어 보기의 최근 주문이 표시되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Orders, User Account
role: Admin, Developer
source-git-commit: 0af6ab4ef15e8aa56354886b341b70a080662eae
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# ACSD-65202: [!UICONTROL My Account] 페이지에 다른 스토어 보기의 최근 주문이 표시되지 않습니다.

ACSD-65202 패치는 **[!UICONTROL My Account]** 페이지에 동일한 저장소 내의 다른 저장소 보기의 최근 주문이 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65202입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p12

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 계정 페이지(섹션 **[!UICONTROL My Account]**)로 이동하면 다른 스토어 보기에 최근 주문이 표시되지 않습니다. 하지만 주문 내역(섹션 *[!UICONTROL My Orders]*)으로 이동하면 두 스토어 보기에서 모두 주문이 표시됩니다.

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. *관리자* 패널에서 새 스토어 보기를 만들고 해당 코드를 *초*(으)로 입력하여 보기를 식별합니다.
1. 간단한 제품을 만들고 색인을 다시 지정합니다.
1. 고객 계정을 만들고 코드가 *default*&#x200B;인 기본 스토어 보기에서 주문을 합니다.
1. **[!UICONTROL My Orders]** 페이지로 이동하여 두 스토어 보기에 모두 순서가 표시되는지 확인합니다. 예:
1. 기본값: https://localhost/pub/default/sales/order/history/
1. 두 번째: https://localhost/pub/second/sales/order/history/

1. 두 스토어 보기에서 **[!UICONTROL My Account]** 페이지로 이동:
1. 기본값: https://localhost/pub/default/customer/account/
1. 두 번째: https://localhost/pub/second/customer/account/

<u>예상 결과</u>:

주문 페이지의 두 스토어 보기에서 주문을 볼 수 있습니다. 같은 가게인데, 다른 가게 경치예요.

<u>실제 결과</u>:

동작이 일관적이지 않습니다. 주문이 두 번째 스토어 보기에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
