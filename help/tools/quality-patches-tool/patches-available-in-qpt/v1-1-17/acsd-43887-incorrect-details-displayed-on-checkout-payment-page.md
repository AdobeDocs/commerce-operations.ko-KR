---
title: 'ACSD-43887: 체크아웃 결제 페이지에 잘못된 세부 정보가 표시됨'
description: ACSD-43887 패치는 회사의 구매 발주가 활성화되면 체크아웃 결제 페이지에 잘못된 세부 정보가 표시되는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-43887입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# ACSD-43887: 체크아웃 결제 페이지에 잘못된 세부 정보가 표시됨

ACSD-43887 패치는 회사의 구매 발주가 활성화되면 체크아웃 결제 페이지에 잘못된 세부 정보가 표시되는 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-43887입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사에 대한 구매 발주가 활성화되면 잘못된 세부 정보가 체크아웃 결제 페이지에 표시됩니다.

<u>필수 구성 요소</u>:

1. B2B 모듈이 설치되어 있습니다.
1. 회사 사용이 _예_(으)로 설정되어 있습니다. **스토어** > **구성** > **일반** > **B2B 기능** > **회사 사용** > **예**(으)로 이동합니다.
1. 구매 주문 사용이 _예_(으)로 설정되어 있습니다. **주문 승인 구성** > **구매 주문 사용** > **예**(으)로 이동합니다.
1. PayPal Express는 결제 방법으로 구성됩니다.

<u>재현 단계</u>:

1. 가상 제품을 만듭니다.
1. 프론트엔드에서 회사 계정을 회사 관리자에게 등록합니다.
1. 백엔드에서 회사 계정을 승인하고 회사를 승인하는 동안 **구매 주문 활성화**&#x200B;를 _예_(으)로 설정합니다.
1. 프론트엔드로 이동한 다음 2단계에서 만든 회사 관리자 계정을 사용하여 로그인합니다.
1. 회사에 대한 &quot;기본 사용자&quot;를 만듭니다. **회사 사용자** > **새 사용자 추가**(으)로 이동합니다.
1. 회사에 대한 &quot;승인 규칙&quot;을 만듭니다. **승인 규칙** > **새 규칙 추가**(으)로 이동합니다.

   * 규칙 유형: 주문 합계
   * 주문 합계: $1 이상입니다.
   * 승인 필요: 회사 관리자

1. 로그아웃한 후 &quot;기본 사용자&quot; 계정을 사용하여 로그인합니다.
1. 1단계에서 만든 가상 제품을 장바구니에 추가하고 체크아웃을 진행합니다.
1. 결제 방법으로 PayPal Express를 선택하고 **구매 주문**&#x200B;을 클릭하세요.
1. 회사 관리자 계정을 사용하여 로그아웃한 후 로그인합니다.
1. **내 구매 주문**(으)로 이동한 다음 **회사 구매 주문**&#x200B;에서 9단계에서 만든 주문에 대한 **보기**&#x200B;를 클릭합니다.
1. 구매 주문을 승인합니다. 구매 발주 상태는 &quot;승인됨: 지급 대기 중&quot;이어야 합니다.
1. 회사 &quot;기본 사용자&quot; 계정을 사용하여 로그아웃하고 로그인합니다.
1. **내 구매 주문** > **보기** > **주문**(으)로 이동합니다.
1. **주문 요약**&#x200B;을 확인하세요.

<u>예상 결과</u>:

주문 요약에는 0이 아닌 올바른 값이 표시됩니다.

<u>실제 결과</u>:

주문 요약 합계 값은 0입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
