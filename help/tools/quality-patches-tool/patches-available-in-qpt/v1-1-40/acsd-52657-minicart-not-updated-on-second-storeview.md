---
title: 'ACSD-52657: 미니마트가 하위 도메인을 사용하는 두 번째 상점 보기에서 업데이트되지 않음'
description: ACSD-52657 패치를 적용하여 하위 도메인을 사용하는 두 번째 저장소 보기에서 미니 마트가 업데이트되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart
role: Admin, Developer
exl-id: feec9dde-5532-481b-9410-7f6be9df4be7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52657: 미니마트가 하위 도메인을 사용하는 두 번째 상점 보기에서 업데이트되지 않음

ACSD-52657 패치는 하위 도메인을 사용하는 두 번째 저장소 보기에서 미니 마트가 업데이트되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52657입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

미니카트는 하위 도메인을 사용하는 보조 저장고에서 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 두 번째 스토뷰를 만들고 기본 URL에 대한 하위 도메인을 구성합니다.
1. 공통 도메인을 갖도록 쿠키 도메인을 업데이트합니다.
1. 기본 스토어에서 장바구니에 제품을 추가합니다.
1. 두 번째 상점 보기를 새로 고친 다음 장바구니 페이지로 이동합니다.

<u>예상 결과</u>:

장바구니와 미니마트는 하위 도메인에서 업데이트됩니다.

<u>실제 결과</u>:

보조 스토어를 새로 고치면 Minicart가 업데이트되지 않지만 장바구니 페이지에 추가된 제품이 표시되며 해당 세션에서 주문할 수 있습니다(`PHPSESSID` 쿠키가 공유됨).

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
