---
title: 'ACSD-64732: 타사 컨트롤러가 고객 세그먼트와 함께 올바르게 캐시되지 않음'
description: ACSD-64732 패치를 적용하여 서드파티 컨트롤러가 고객 세그먼트에서 올바르게 캐시되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Cache
role: Admin, Developer
exl-id: 378e5a96-06dd-4796-9e45-a67cf539fcce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-64732: 타사 컨트롤러가 고객 세그먼트와 함께 올바르게 캐시되지 않음

ACSD-64732 패치는 타사 컨트롤러가 고객 세그먼트에서 올바르게 캐시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-64732입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

타사 컨트롤러가 고객 세그먼트에서 올바르게 캐시되지 않습니다.

<u>재현 단계</u>:

1. 사용자 지정 컨트롤러(/catalog/category/vary)로 이동합니다.
1. **[!UICONTROL Network]** 탭으로 이동하여 **[!DNL X-Magento-Vary]**&#x200B;의 값을 확인합니다.

<u>예상 결과</u>:

**[!UICONTROL X-Magento-Vary]** 값은 사용자 지정 컨트롤러에서 동일해야 합니다.

<u>실제 결과</u>:

**[!UICONTROL X-Magento-Vary]**&#x200B;의 값이 다르므로 캐시 누락이 발생합니다. 즉, 사용자 지정 컨트롤러를 방문할 때 이전에 생성된 캐시를 사용할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
