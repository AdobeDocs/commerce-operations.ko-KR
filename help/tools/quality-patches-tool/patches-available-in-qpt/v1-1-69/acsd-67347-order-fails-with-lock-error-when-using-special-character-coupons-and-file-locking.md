---
title: 'ACSD-67347: 쿠폰 코드를 사용할 때 "잠금을 획득할 수 없습니다" 오류와 함께 주문이 실패합니다'
description: '쿠폰 코드에 특수 문자(예: BIT/123456)가 포함되어 있고 파일 잠금이 활성화되어 있을 때 "잠금을 획득할 수 없음" 오류와 함께 주문이 실패하는 Adobe Commerce 문제에 ACSD-67347 패치를 적용합니다.'
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347: 쿠폰 코드를 사용할 때 *잠금을 획득할 수 없음* 오류가 발생하여 주문이 실패합니다.

ACSD-67347 패치는 쿠폰 코드에 특수 문자(예: BIT/123456)가 포함되어 있고 파일 잠금이 활성화되어 있을 때 주문이 *잠금을 얻을 수 없음* 오류와 함께 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-67347입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p12

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특수 문자가 포함된 쿠폰을 사용하고 파일 잠금이 활성화된 경우 *잠금을 획득할 수 없습니다* 오류가 발생하여 주문이 실패합니다.

<u>재현 단계</u>:

1. 2.4-develop을 설치합니다.
1. `env.php` 파일에서 파일 잠금 구성을 설정합니다.

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. 쿠폰 코드 형식 *BIT/123456*&#x200B;을(를) 사용하여 쿠폰이 포함된 장바구니 규칙을 만듭니다.
1. 간단한 제품을 만듭니다.
1. 제품을 장바구니에 추가하고 쿠폰 코드를 적용합니다.
1. 체크아웃을 진행하고 주문합니다.

<u>예상 결과</u>:

쿠폰 코드를 만드는 데 아무런 제약이 없기 때문에 주문이 성공적으로 이루어졌습니다.

<u>실제 결과</u>:

주문을 할 수 없습니다. 다음 오류가 나타납니다. *잠금을 획득할 수 없습니다.*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
