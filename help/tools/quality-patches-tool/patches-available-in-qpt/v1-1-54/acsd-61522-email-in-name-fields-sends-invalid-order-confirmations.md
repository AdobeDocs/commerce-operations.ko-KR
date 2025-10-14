---
title: 'ACSD-61522: *이름 및 성* 필드의 이메일 주소에서 잘못된 주문 확인을 보냅니다.'
description: ACSD-61522 패치를 적용하여 게스트 고객의 *[!UICONTROL First Name]* 및 *[!UICONTROL Last Name]* 필드에 이메일 주소를 입력할 수 있어 잘못된 주문 확인 이메일이 전송되는 Adobe Commerce 문제를 해결합니다.
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522: *이름 및 성* 필드에 있는 전자 메일 주소에서 잘못된 주문 확인을 보냅니다.

ACSD-61522 패치는 게스트 고객의 *[!UICONTROL First Name]* 및 *[!UICONTROL Last Name]* 필드에 전자 메일 주소를 입력할 수 있어 잘못된 주문 확인 전자 메일이 전송되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61522입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p9

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

시스템에서 게스트 고객의 *[!UICONTROL First Name]* 및 *[!UICONTROL Last Name]* 필드에 전자 메일 주소를 입력할 수 있으므로 잘못된 주문 확인 전자 메일이 전송됩니다.

<u>재현 단계</u>:

1. 장바구니에 제품을 게스트 고객으로 추가합니다.
1. **[!UICONTROL Checkout]**(으)로 이동합니다.
1. *[!UICONTROL Email Address]* 필드를 *test1@example.com*(으)로 채웁니다.
1. *[!UICONTROL First Name]* 필드를 *<test2@example.com>*(으)로 채웁니다.
1. *[!UICONTROL Last Name]*&#x200B;을(를) *<test3@example.com>*(으)로 채웁니다.
1. 다른 필수 필드를 채웁니다.
1. 주문하십시오.

<u>예상 결과</u>:

*[!UICONTROL First Name]* 및 *[!UICONTROL Last Name]* 필드에서는 전자 메일 주소를 사용할 수 없습니다.

<u>실제 결과</u>:

1. 주문이 완료되었습니다.
1. *[!UICONTROL First Name]* 및 *[!UICONTROL Last Name]* 필드가 입력한 대로 저장됩니다.
1. 주문 확인 이메일은 세 개의 이메일 모두에 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
