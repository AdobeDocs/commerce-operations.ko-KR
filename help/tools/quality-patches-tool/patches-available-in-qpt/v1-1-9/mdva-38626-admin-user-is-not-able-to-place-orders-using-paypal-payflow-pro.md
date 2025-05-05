---
title: 'MDVA-38626: 관리자가 PayPal Payflow Pro를 사용하여 주문을 할 수 없음'
description: MDVA-38626 패치는 관리자 사용자가 PayPal Payflow Pro 결제 방법을 사용하여 백엔드에 주문할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38626입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Admin Workspace, Orders, Payments
role: Admin
exl-id: 32d2e5dd-7081-42f2-a074-71e21c870dc2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-38626: 관리자가 PayPal Payflow Pro를 사용하여 주문을 할 수 없음

MDVA-38626 패치는 관리자 사용자가 PayPal Payflow Pro 결제 방법을 사용하여 백엔드에 주문할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38626입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 사용자는 PayPal Payflow Pro 결제 방법을 사용하여 백엔드에 주문을 할 수 없습니다.

<u>재현 단계</u>:

1. PayPal Payflow Pro 결제 방법을 구성합니다.
1. **고객** > **모든 고객**(으)로 이동하여 고객 계정을 만듭니다.
1. **순서 만들기**&#x200B;를 클릭합니다.
1. 장바구니에 품목을 추가합니다.
1. Payflow Pro를 사용하여 주문해 보십시오.

<u>예상 결과</u>:

주문이 완료되었습니다.

<u>실제 결과</u>:

사용자에게 500 오류가 발생합니다. 보고서 로그에는 다음이 포함됩니다.

```
{"0":"No such entity with cartId = 0","1":"#1 Magento\\Quote\\Model\\QuoteRepository->loadQuote() called at [app\/code\/Magento\/Quote\/Model\/QuoteRepository.php:136]\n#2 Magento\\Quote\\Model\\QuoteRepository->get() called at [lib\/internal\/Magento\/Framework\/Interception\/Interceptor.php:58]\n#3 Mag
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
