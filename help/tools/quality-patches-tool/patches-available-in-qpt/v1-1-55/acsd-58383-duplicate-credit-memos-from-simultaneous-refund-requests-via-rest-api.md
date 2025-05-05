---
title: 'ACSD-58383:  [!DNL REST API]을(를) 통한 동시 환불 요청에서 중복된 대변 메모'
description: ACSD-58383 패치를 적용하여 동시에 실행되는 두 개의 동일한 요청으로  [!DNL REST API] 을(를) 통해 환불을 발행하면 중복 대변 메모가 생성되는 Adobe Commerce 문제를 해결합니다.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: d3d98c04afe32d80cdf985b1d93c8a2cb57236ed
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-58383: [!DNL REST API]을(를) 통한 동시 환불 요청에서 중복된 대변 메모

ACSD-58383 패치는 동시에 실행되는 두 개의 동일한 요청으로 [!DNL REST API]을(를) 통해 환불을 발행하면 크레딧 메모가 중복되는 문제를 해결합니다.

이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-58383입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

중복 대변 메모는 두 개의 환불이 동시에 생성되므로 발생합니다.

<u>재현 단계</u>:

1. Commerce [!UICONTROL Admin]에서 [!DNL Paypal Express]을(를) 구성합니다.
1. 결제 동작을 *판매*(으)로 설정합니다.
1. [!DNL PayPal] 샌드박스 웹 사이트에서 [!DNL PayPal] IPN(즉시 결제 알림)을 구성합니다.
1. [!DNL PayPal] 샌드박스 웹 사이트에서 환불 문제를 해결합니다.
1. 개발자 도구를 사용하여 [!DNL PayPal]에서 IPN 메시지를 에뮬레이션합니다. IPN은 대변 메모를 작성해야 합니다.
1. [!DNL API] 통화를 사용하여 두 번째 대변 메모를 만듭니다.

<u>예상 결과</u>:

동일한 항목에 대해 하나의 대변 메모만 생성됩니다.


<u>실제 결과</u>:

동일한 품목에 대해 두 개의 대변 메모가 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
