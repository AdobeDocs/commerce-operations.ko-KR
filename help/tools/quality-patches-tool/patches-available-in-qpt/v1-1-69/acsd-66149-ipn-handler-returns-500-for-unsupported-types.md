---
title: 'ACSD-66149: IPN 처리기가 지원되지 않는 유형에 대해 *500*을 반환합니다.'
description: ACSD-66149 패치를 적용하여 IPN 핸들러가 지원되지 않거나 알 수 없는 IPN 유형을 무시하지 않아 문제가 기록되지 않고 프로세스가 중단되며 500 오류가 반환되는 Adobe Commerce 문제를 해결합니다.
feature: Payments
role: Admin, Developer
source-git-commit: 81e8bf62c026023f71d52c219357bd7911275f69
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-66149: IPN 처리기가 지원되지 않는 형식에 대해 *500*&#x200B;을(를) 반환합니다.

ACSD-66149 패치는 IPN(즉시 결제 알림) 처리기가 지원되지 않거나 알 수 없는 IPN 유형에 대해 *500* 오류를 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66149입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

지원되지 않거나 알 수 없는 IPN 형식에 대해 IPN 처리기가 *500* 오류를 반환하는 문제가 있습니다. 이는 Paypal이 일부 필드가 누락된 상태로 IPN을 전송할 때 발생합니다.

<u>재현 단계</u>:

1. PayPal에서 알 수 없는 모든 종류의 IPN 유형을 에뮬레이션하는 사용자 지정 모듈을 만듭니다.
1. 제품을 하나 이상 만듭니다.
1. 자체 자격 증명으로 PayPal Express를 구성합니다.
1. Paypal Express로 주문하세요.
1. PayPal 에뮬레이터를 실행합니다.

<u>예상 결과</u>:

응용 프로그램 IPN 처리기가 잘못된 IPN 형식을 무시하고 *500* 오류를 생성하지 않습니다.

```Order 000000001: Status processing — HTTP 500```

<u>실제 결과</u>:

응용 프로그램에서 잘못된 IPN을 처리하는 동안 많은 *500* 오류가 발생하며, 필요한 필드가 없으면 가끔 일부 주문을 처리하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko)

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
