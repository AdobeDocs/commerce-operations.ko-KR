---
title: 'ACSD-67264: 번들 및 다운로드 가능한 제품 페이지 레이아웃이 여러 장치에서 일관되지 않음'
description: ACSD-67264 패치를 적용하여 제품 정보 미디어 블록의 재배열로 인해 발생한 Adobe Commerce 번들 및 다운로드 가능한 페이지 레이아웃 문제를 해결합니다.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264: 번들 및 다운로드 가능한 제품 페이지 레이아웃이 여러 장치에서 일관되지 않음

ACSD-67264 패치는 번들 및 다운로드 가능한 제품 페이지 레이아웃이 장치 간에 일치하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-67264입니다. 이 문제는 Adobe Commerce 2.4.8에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

번들 및 다운로드 가능한 제품 페이지에서 제품 정보 미디어 블록의 재배열로 인해 레이아웃 문제가 발생했습니다.

<u>재현 단계</u>:

1. 샘플 데이터를 설치합니다.
1. 번들 제품 페이지를 열고 바탕 화면의 레이아웃을 확인합니다.
1. 번들 제품 페이지를 위시리스트에 추가하고 위시리스트로 이동한 후 편집 아이콘을 클릭하고 레이아웃을 확인합니다.
1. 다운로드 가능한 제품에 대해 2단계와 3단계를 반복합니다.

<u>예상 결과</u>:

번들 제품 PDP는 문제 없이 렌더링됩니다.

<u>실제 결과</u>:

번들 제품 PDP는 임의의 공백으로 렌더링됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko)

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
