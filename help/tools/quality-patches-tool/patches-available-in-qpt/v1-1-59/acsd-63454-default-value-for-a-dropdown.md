---
title: 'ACSD-63454: 드롭다운 및 다중 선택 속성의 기본값이 데이터베이스에 제대로 저장되지 않았습니다.'
description: ACSD-63454 패치를 적용하여 드롭다운 및 다중 선택 속성에 대한 기본값이 데이터베이스에 제대로 저장되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454: [!UICONTROL Dropdown] 및 [!UICONTROL Multiple Select] 특성에 대한 기본값이 데이터베이스에 제대로 저장되지 않았습니다.

ACSD-63454 패치는 [!UICONTROL Dropdown] 및 [!UICONTROL Multiple Select] 특성에 대한 기본값이 데이터베이스에 제대로 저장되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63454입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Dropdown] 및 [!UICONTROL Multiple Select] 특성의 기본값이 데이터베이스에 올바르게 저장되지 않았습니다. 기본값을 업데이트하는 대신 새 값이 이전 값에 쉼표로 구분되어 추가됩니다.

<u>재현 단계</u>:

1. 백엔드에 로그인하고 **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**(으)로 이동합니다.
1. **[!UICONTROL Add New Attribute]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Properties]** 탭에서 다음을 설정합니다.
   * **[!UICONTROL Default Label]**: *테스트*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**: **[!UICONTROL Is Default]**&#x200B;을(를) 선택하지 않고 두 옵션을 추가하십시오.
1. **[!UICONTROL Save Attribute]**&#x200B;을(를) 클릭합니다.
1. 데이터베이스에서 `default_value` 열이 비어 있는지 확인합니다.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. 돌아가서 두 옵션 중 하나를 **[!UICONTROL Is Default]**(으)로 설정합니다.
1. 이제 `default_value`에 선택한 옵션 ID가 포함되어 있는지 데이터베이스를 다시 확인하십시오.
1. 뒤로 돌아가서 다른 옵션을 선택하여 기본 옵션을 변경합니다.

<u>예상 결과</u>:

새 기본값이 데이터베이스의 이전 값을 대체해야 합니다.

<u>실제 결과</u>:

기본값을 새 값으로 바꾸는 대신 새 값을 이전 값에 쉼표로 구분하여 추가합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
