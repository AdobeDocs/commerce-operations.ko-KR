---
title: 'ACSD-61969: 대문자 또는 소문자로 구성된 쿠폰 코드를 입력하는 데 필요합니다.'
description: ACSD-61969 패치를 적용하여 사용자가 쿠폰 코드를 대문자 또는 소문자로 구성한 대로 정확히 입력해야 하는 Adobe Commerce 문제를 해결할 수 있습니다.
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: 대문자 또는 소문자로 구성된 쿠폰 코드를 입력하는 데 필요합니다.

ACSD-61969 패치는 사용자가 쿠폰 코드를 대문자 또는 소문자로 구성된 것과 정확히 동일하게 입력해야 하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61969입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

백엔드에서 쿠폰 코드를 적용할 때 대문자 또는 소문자로 구성된 것과 정확히 동일하게 입력해야 합니다. 관리자는 관리자 주문 생성에서 대/소문자를 구분하지만 상점에서는 대/소문자를 구분하지 않습니다.

<u>재현 단계</u>:

1. 특정 쿠폰 *[!UICONTROL Cart Price Rule]* TEST *을(를) 사용하여*&#x200B;을(를) 만듭니다. 쿠폰 코드가 대문자로 되어 있는지 확인하십시오.
1. 관리자에서 주문을 만듭니다.
1. *필드에* test *[!UICONTROL Apply Coupon Code]*&#x200B;을(를) 추가하고 필드 근처의 화살표를 클릭하여 쿠폰을 적용합니다.
1. 결과를 확인합니다.

<u>예상 결과</u>:

쿠폰이 정상적으로 적용되었습니다. 쿠폰 필드는 대/소문자를 구분하지 않습니다.

<u>실제 결과</u>:

쿠폰이 적용되지 않았습니다 다음 오류가 표시됩니다.

*테스트 쿠폰 코드가 잘못되었습니다. 코드를 확인하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
