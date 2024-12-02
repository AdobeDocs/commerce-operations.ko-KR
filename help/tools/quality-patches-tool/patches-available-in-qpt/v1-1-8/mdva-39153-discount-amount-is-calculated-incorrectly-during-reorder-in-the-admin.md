---
title: 'MDVA-39153: 관리자에서 재주문 중에 할인 금액이 잘못 계산됨'
description: MDVA-39153 패치는 관리자에서 재정렬을 수행하는 동안 할인 금액이 잘못 계산되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39153입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153: 관리자에서 재주문 중에 할인 금액이 잘못 계산됨

MDVA-39153 패치는 관리자에서 재정렬을 수행하는 동안 할인 금액이 잘못 계산되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39153입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자의 순서 재지정 중에 할인 금액이 잘못 계산되었습니다.

<u>재현 단계</u>:

1. **관리자** > **스토어** > **구성** > **판매** > **세금**&#x200B;으로 이동합니다.
1. 장바구니에 세금을 표시하는 배송세를 켭니다.
1. 테이블 요금 배송 방법($15)을 활성화하고 구성합니다.
1. 기본 제공 세율에 대한 세금 규칙을 만듭니다(CA의 경우).
1. 전체 장바구니와 배송 금액에 고정 $5 할인이 적용된 장바구니 가격 규칙을 만듭니다.
1. 가격이 $12인 제품을 장바구니에 추가하고 장바구니 페이지로 이동합니다.
1. 장바구니에 할인을 적용합니다.
1. &quot;예상&quot; 섹션의 배송 방법을 &quot;고정 요금&quot;으로 설정합니다.
1. 검토 단계까지 체크아웃을 진행합니다(주문하지 마십시오).
1. 홈페이지로 이동한 다음 장바구니로 돌아갑니다.
1. &quot;예상&quot; 섹션의 배송 방법을 &quot;테이블 요금&quot;으로 변경합니다.

<u>예상 결과</u>:

할인은 그대로 5달러입니다

<u>실제 결과</u>:

할인은 6달러 31센트입니다

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
