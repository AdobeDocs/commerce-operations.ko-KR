---
title: 'ACSD-62355: Adobe Commerce에서 구성 가능한 제품 편집 성능 개선'
description: ACSD-62355 패치를 적용하여 제품이 많은 값을 갖는 수많은 속성을 기반으로 할 때 구성 가능한 제품 편집 페이지에 느린 로드가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace
role: Admin, Developer
exl-id: cd934aa9-901a-4f03-ab83-716131e6bd85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355: Adobe Commerce에서 구성 가능한 제품 편집 성능 개선

ACSD-62355 패치는 제품에 많은 값이 있는 속성이 있을 때 구성 가능한 제품 편집 페이지에서 로딩 시간이 느리고 메모리 소비가 많은 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62355입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품 편집 페이지는 구성 가능한 제품이 값이 많은 여러 속성을 기반으로 할 때 로드하는 데 시간이 오래 걸려 지연과 잠재적 시간 초과 또는 메모리 제한 문제가 발생합니다.

<u>재현 단계</u>:

1. 기본 특성 집합에 각각 [!UICONTROL Filterable]이고 [!UICONTROL Scope]이(가) 있는 9개의 새 특성을 만듭니다. [!UICONTROL Global].
   * 속성 1: 50개 옵션
   * 속성 2: 20개 옵션
   * 속성 3: 10 옵션
   * 속성 4: 5개 옵션
   * 속성 5: 5개 옵션
   * 속성 6: 5개 옵션
   * 속성 7: 5개 옵션
   * 속성 8: 3개 옵션
   * 속성 9: 2개 옵션

1. 새로 만든 속성의 옵션 조합으로 9개의 간단한 제품을 만듭니다.
   * 제품 1: 각 속성의 첫 번째 옵션
   * 제품 2: 각 속성의 두 번째 옵션
   * 제품 3: 각 속성의 세 번째 옵션
   * 제품 4: 각 속성의 네 번째 옵션
   * 속성에 제품 수보다 적은 옵션이 있는 경우 나머지 제품을 해당 속성 내의 임의 옵션에 할당합니다.

1. 새로 만든 속성을 사용하는 구성 가능한 제품을 만듭니다.
   * 다음 구성으로 하나의 하위 제품을 추가합니다.
      * 속성 1의 마지막 옵션과 속성 2에서 9까지의 첫 번째 옵션을 사용합니다.
      * 이렇게 하면 구성 가능한 제품이 1개 있고 하위 제품이 1개 있습니다.
1. 구성 가능한 제품의 **[!UICONTROL Configurations]** 탭으로 이동합니다.
1. **[!UICONTROL Add Products]**&#x200B;을(를) 수동으로 클릭하고 이전에 만든 간단한 제품을 하나씩 추가합니다.
1. 추가할 때마다 변경 내용을 저장합니다.
1. 제품을 추가할 때 구성 가능한 제품 편집 페이지가 로드되는 시간을 확인합니다.
1. 7개의 제품을 추가한 후에는 RAM 사용량과 페이지 로드 시간이 크게 늘어났습니다

<u>예상 결과</u>:

제품 편집 양식은 과도한 메모리 소모 없이 빠르고 효율적으로 로드되어야 합니다.

<u>실제 결과</u>:

구성 가능한 제품을 편집하는 것은 로드하는 데 시간이 오래 걸리고 메모리 제한 또는 시간 초과 오류가 발생할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
