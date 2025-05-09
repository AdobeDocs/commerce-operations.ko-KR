---
title: 'ACSD-64592: 비기본 스토어 기프트 카드 청구 링크 기본 웹 사이트로 리디렉션'
description: 다중 웹 사이트 설정에서 가상 선물 카드를 보조(기본값이 아닌) 웹 사이트에서 구매할 때 이메일의 선물 카드 코드 링크에 기본 웹 사이트 URL이 있는 문제를 해결하려면 ACSD-64592 패치를 적용합니다.
feature: Gift, Products
role: Admin, Developer
source-git-commit: 39866e1cf8f2afd892c9e151259a446d0277d58f
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# ACSD-64592: 비기본 스토어 기프트 카드 청구 링크 기본 웹 사이트로 리디렉션

ACSD-64592 패치는 다중 사이트 환경에서 가상 기프트 카드를 보조(기본이 아닌) 웹 사이트에서 구매하는 경우 기프트 카드 코드 링크가 포함된 이메일이 사용자를 기본 웹 사이트의 URL로 안내하는 문제를 해결합니다. 이 문제는 Adobe Commerce 2.4.9에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다중 웹 사이트 설정에서 가상 기프트 카드를 보조(기본값이 아닌) 사이트에서 구매하면 기프트 카드 코드 링크가 포함된 이메일이 사용자를 기본 웹 사이트의 URL로 안내합니다.

<u>재현 단계</u>:

1. 보조 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 기본 및 보조 웹 사이트에 대해 서로 다른 기본 URL을 구성합니다.
1. 일부 금액 옵션을 사용하여 가상 기프트 카드를 만드십시오.
1. **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**&#x200B;에서 새 코드 풀을 생성합니다.
1. 상품권 제품을 2차 웹사이트에서 주문하세요.
1. Commerce 관리자에서 주문에 대한 송장을 발행합니다.
1. *Two*(으)로부터 선물을 받았습니다. 기프트 카드 코드 링크에서 URL을 확인하십시오.

<u>예상 결과</u>:

기프트 카드 코드 링크에는 두 번째 웹 사이트 링크가 있어야 합니다.

<u>실제 결과</u>:

주문이 두 번째 웹 사이트에 배치되더라도 기프트 카드 코드 링크에는 기본 웹 사이트 URL이 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.
* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
