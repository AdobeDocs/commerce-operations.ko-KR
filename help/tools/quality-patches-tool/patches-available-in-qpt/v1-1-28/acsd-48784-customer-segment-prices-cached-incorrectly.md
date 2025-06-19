---
title: 'ACSD-48784: 고객 그룹 간에 잘못 캐시된 고객 세그먼트 가격'
description: ACSD-48784 패치를 적용하여 고객 그룹 간에 고객 세그먼트 가격이 잘못 캐시되는 Adobe Commerce 문제를 수정합니다.
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
exl-id: a691c61c-fdba-4d6a-8314-095dfb0ba4a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48784: 고객 그룹 간에 잘못 캐시된 고객 세그먼트 가격

ACSD-48784 패치는 고객 그룹 간에 고객 세그먼트 가격이 잘못 캐시되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48784입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 그룹 간에 고객 세그먼트 가격이 잘못 캐시됩니다.

<u>필수 구성 요소</u>:

[!DNL Varnish] 또는 [!DNL Fastly] 구성

<u>재현 단계</u>:

1. 스토어에서 전체 페이지 캐싱을 활성화합니다.
1. 특별 고객 그룹 가격을 가진 사용자로 사이트에 로그인합니다.
1. 특별 고객 그룹 가격이 적용된 제품에 대한 제품 페이지로 이동합니다. *특별 가격*&#x200B;을 확인하세요.
1. 별도의 브라우저에서 로그인하지 않고 게스트 사용자와 동일한 제품 페이지를 엽니다. 정가를 지켜라.
1. Adobe Commerce 관리 인터페이스에 액세스하여 이 저장소에 대한 Adobe Commerce 및 [!DNL Fastly] 캐시를 지우십시오.
1. 로그인한 브라우저에서 `X-Magento-Vary` 쿠키를 제거합니다.
1. 로그인한 브라우저에서 캐싱이 완전히 플러시될 때까지 동일한 제품 페이지를 여러 번 다시 로드합니다.
1. 로그인하지 않은 브라우저에서 제품 페이지를 다시 로드하여 이제 고객 그룹 가격을 확인합니다.

<u>예상 결과</u>:

제품 페이지에는 특정 고객 그룹에 대한 올바른 가격이 표시됩니다.

<u>실제 결과</u>:

* 게스트 사용자에게는 특별한 로그인 사용자 가격이 표시됩니다.
* 제품이 추가되면 미니 장바구니에 정확한 가격이 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
