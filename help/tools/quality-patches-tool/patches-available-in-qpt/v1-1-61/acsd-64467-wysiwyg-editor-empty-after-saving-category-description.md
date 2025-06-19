---
title: 'ACSD-64467: 스토어 보기 수준에서 카테고리 설명을 저장한 후 WYSIWYG 편집기가 비어 있음'
description: ACSD-64467 패치를 적용하여 스토어 보기 수준에서 카테고리 설명을 저장한 후 WYSIWYG 편집기가 비어 있는 것으로 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: 스토어 보기 수준에서 카테고리 설명을 저장한 후 WYSIWYG 편집기가 비어 있음

ACSD-64467 패치는 스토어 보기 수준에서 카테고리 설명을 저장한 후 WYSIWYG 편집기가 비어 있는 것으로 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64467입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스토어 보기 수준에서 카테고리 설명을 저장한 후 WYSIWYG 편집기가 비어 있습니다.

<u>재현 단계</u>:

1. 스토어 보기 수준의 Commerce 관리에서 카테고리를 편집합니다.
1. 범주 설명 옆에 있는 *[!UICONTROL Use default value]* 확인란의 선택을 취소하십시오.
1. WYSIWYG 편집기에 설명을 입력합니다.
1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

설명이 저장되고 올바르게 표시됩니다.

<u>실제 결과</u>:

페이지를 다시 로드하면 설명이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
