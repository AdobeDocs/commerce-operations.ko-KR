---
title: 'ACSD-44591: CAPTCHA 확인 없이 주문할 때 오류 발생'
description: ACSD-44591 패치는 CAPTCHA 확인 없이 주문을 하려고 할 때 사용자가 오류가 발생하는 문제를 해결합니다.
feature: Orders
role: Admin
exl-id: 4b8a8090-a2ba-428c-9a04-7c0842e94a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-44591: CAPTCHA 확인 없이 주문할 때 오류 발생

ACSD-44591 패치는 CAPTCHA 확인 없이 주문을 하려고 할 때 사용자가 오류가 발생하는 문제를 해결합니다.
이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-44591입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 CAPTCHA 확인 없이 주문하려고 할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. Google ReCaptcha v2(로봇이 아님)를 구성합니다.
1. 체크아웃을 위해 ReCaptcha를 활성화합니다.
1. ReCaptcha를 클릭하지 않고 주문해 보십시오.
1. 누락된 ReCaptcha(*ReCaptcha 유효성 검사 실패)에 대한 오류 메시지가 표시되면 다시 시도하십시오*), **ReCaptcha**&#x200B;를 클릭한 다음 주문을 시도하십시오.

<u>예상 결과</u>:

주문은 잘못된 ReCaptcha와 함께 제공되지 않습니다.

<u>실제 결과</u>:

다음과 같은 오류가 발생합니다.

* *ReCaptcha 유효성 검사에 실패했습니다. 다시 시도해 주십시오.*
* *ID = 1*&#x200B;인 장바구니 없음

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
