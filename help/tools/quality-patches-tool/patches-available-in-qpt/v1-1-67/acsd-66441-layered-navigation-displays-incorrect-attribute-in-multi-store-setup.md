---
title: 'ACSD-66441: 다중 저장소 설정에 계층 탐색에 잘못된 속성 옵션이 표시됨'
description: ACSD-66441 패치를 적용하여 다중 스토어 설정에서 계층 탐색이 다른 스토어의 속성을 잘못 표시하는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5a8b30d1fac953ff5d921b7a7d3f12619b03bc81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# ACSD-66441: 다중 저장소 설정에 계층 탐색에 잘못된 속성 옵션이 표시됨

ACSD-66441 패치는 다중 스토어 설정에서 계층화된 탐색이 다른 스토어의 속성을 잘못 표시하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66441입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

현재 스토어 보기에서 해당 제품을 사용할 수 없는 경우에도 스토어프론트의 계층화된 탐색에는 다른 스토어의 속성 값이 포함됩니다.

<u>재현 단계</u>:

1. 보조 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 사용자 지정 속성(예: 크기)을 사용하여 구성 가능한 제품을 만듭니다.
1. 구성 가능한 제품을 기본 웹 사이트 및 카테고리에 할당합니다.
1. 모든 데이터를 다시 색인화합니다.
1. 상점 첫 화면에서 할당된 카테고리로 이동합니다. 모든 크기 옵션이 레이어 탐색에 올바르게 표시됩니다.
1. 기본 웹 사이트에서 두 개의 간단한 제품을 할당 해제하고 보조 웹 사이트에 할당하거나 기본 웹 사이트에서 제거합니다.
1. 모든 데이터를 다시 색인화합니다.
1. Storefront 카테고리 페이지를 다시 방문하여 계층화된 탐색을 확인하십시오.

<u>예상 결과</u>:

레이어 탐색에는 현재 스토어 또는 웹 사이트에 할당된 제품의 속성 옵션만 표시됩니다.

<u>실제 결과</u>:

계층화된 탐색은 다른 스토어 또는 웹 사이트에 할당된 제품의 속성 옵션(크기)을 표시합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
