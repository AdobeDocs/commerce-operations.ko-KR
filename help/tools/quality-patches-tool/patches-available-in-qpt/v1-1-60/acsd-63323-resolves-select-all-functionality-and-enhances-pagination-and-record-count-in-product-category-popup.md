---
title: 'ACSD-63323: [!UICONTROL Select All] 기능을 확인하고 제품 범주 팝업의 페이지 매김 및 레코드 수를 개선합니다.'
description: ACSD-63323 패치를 적용하여 범주에 제품을 추가할 때 [!UICONTROL Select All] 옵션이 작동하지 않는 Adobe Commerce 문제를 해결합니다. 또한 팝업 그리드를 통해 카테고리에 제품을 추가할 때 페이지 매김 및 레코드 수 레이블이 올바르게 작동하는지 확인합니다.
feature: Products
role: Admin, Developer
exl-id: 96e318fd-f1dd-4b15-b171-78ae1c8e4e0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63323: [!UICONTROL Select All] 기능을 확인하고 제품 범주 팝업의 페이지 매김 및 레코드 수를 개선합니다.

ACSD-63323 패치는 범주에 제품을 추가할 때 **[!UICONTROL Select All]** 옵션이 작동하지 않는 문제를 해결합니다. 또한 팝업 그리드를 통해 카테고리에 제품을 추가할 때 페이지 매김 및 레코드 수 레이블이 올바르게 작동하는지 확인합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63323입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 > **[!UICONTROL Select All]** > 범주 선택 > **[!UICONTROL Categories]** > **[!UICONTROL Products in Category]**&#x200B;에서 **[!UICONTROL Add Products]** 옵션이 작동하지 않는 문제를 해결했습니다. 또한 팝업 그리드를 통해 카테고리에 제품을 추가할 때 페이지 매김 및 레코드 수 레이블이 올바르게 작동하는 데 도움이 됩니다.


<u>재현 단계</u>:

1. 다음 명령을 사용하여 *1200* 제품을 생성합니다.

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;을(를) 열고 찾은 제품 수: *1200* 레코드를 확인합니다.
1. 기본 범주 > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**&#x200B;을(를) 엽니다.
1. **[!UICONTROL Assign]** > **[!UICONTROL Select All]**&#x200B;을(를) 클릭합니다.
1. 페이지의 제품 수를 값 = *5*(으)로 변경합니다.


**예상 결과**:

*메시지: 1200개의 레코드를 찾았습니다(1200개가 선택됨)*

**실제 결과**:

* 페이지 매김이 작동하지 않습니다.
* 잘못된 메시지가 표시됩니다. *5*&#x200B;개의 레코드를 찾았습니다(*20*&#x200B;개 선택됨).

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
