---
title: 'ACSD-66082: 제품 가져오기를 통해 제품의 견본 이미지를 업데이트할 수 없음'
description: ACSD-66082 패치를 적용하여 견본 이미지 설정을 해제하기 위해 swatch_image 필드가 EMPTY_VALUE로 설정된 CSV 파일을 업로드하면 오류로 인해 가져오기 프로세스가 실패하는 Adobe Commerce 문제를 해결합니다.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
source-git-commit: e0d2e42b070591f3fefc0e9adb1bf5c1ba580fd9
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-66082: 제품 가져오기를 통해 제품의 견본 이미지를 업데이트할 수 없음

ACSD-66082 패치는 제품 가져오기를 통해 제품의 견본 이미지를 업데이트할 수 없었던 문제를 수정했습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66082입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

견본 이미지 설정을 해제하기 위해 `swatch_image` 필드가 `EMPTY_VALUE`(으)로 설정된 CSV 파일을 업로드하면 오류가 발생하여 가져오기 프로세스가 실패합니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동합니다. **[!UICONTROL Add Product]** 단추 옆에 있는 아래쪽 화살표를 클릭하고 **[!UICONTROL Simple Product]**&#x200B;을(를) 선택합니다. **[!UICONTROL SKU]**&#x200B;을(를) *ABC*(으)로 설정합니다.
1. 이름이 *testing.png*&#x200B;인 PNG 이미지를 `var/import/images/`에 업로드합니다.
1. 다음 내용으로 CSV 파일을 만듭니다.

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. 다음 설정을 조정하여 파일을 가져오려면 **[!UICONTROL System]** > **[!UICONTROL Import]**(으)로 이동하십시오.
   * **[!UICONTROL Entity type]**: *제품*
   * **[!UICONTROL Import Behavior]**: *추가/업데이트*
   * 가져올 이전 단계에서 만든 CSV 파일을 선택하려면 **[!UICONTROL Choose File]**&#x200B;을(를) 클릭하십시오. 가져오기에 성공하고 견본이 추가됩니다.
1. 다음 콘텐츠로 CSV를 업데이트합니다.

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. 가져오기 프로세스를 반복합니다.

<u>예상 결과</u>:

견본 이미지가 설정되지 않았습니다.

<u>실제 결과</u>:

가져오기 프로세스로 인해 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
