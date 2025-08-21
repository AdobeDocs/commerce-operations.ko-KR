---
title: 'ACP2E-3731: [!UICONTROL Catalog, Search] 가시성이 있는 제품 내보내기에 다른 스토어 보기의 레코드가 포함됩니다'
description: ACP2E-3731 패치를 적용하여 가시성 필터가 [!UICONTROL Catalog, Search]​(으)로 설정된 제품 내보내기에 저장소 범위 특성 변형으로 인해 다중 저장소 설정에 잘못된 행이 포함되는 Adobe Commerce을 수정합니다.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731: [!UICONTROL Catalog, Search] 가시성이 있는 제품 내보내기에 다른 스토어 보기의 레코드가 포함됩니다

ACP2E-3731 패치는 *[!UICONTROL Catalog, Search]* 가시성을 가진 제품 내보내기에 다중 스토어 환경의 다른 스토어 조회수의 레코드가 잘못 포함되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3731입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p9

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

저장소 범위 특성 변형으로 인해 다중 저장소 설정에서 가시성 필터가 *[!UICONTROL Catalog, Search]*(으)로 설정된 경우 제품 내보내기에 잘못된 행이 포함됩니다.

<u>재현 단계</u>:

1. 관리 패널에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**(으)로 이동하여 추가 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**(으)로 이동합니다. 특성을 만들려면 **[!UICONTROL Add Attribute Set]**&#x200B;을(를) 클릭하십시오. **[!UICONTROL Based On]**&#x200B;을(를) *기본*(으)로 설정합니다.
1. 제품을 만들고 기본 웹 사이트와 보조 웹 사이트 모두에 할당합니다.
1. **[!UICONTROL Scope]**&#x200B;이(가) *모든 저장소 보기*(으)로 설정된 새로 만든 특성에 대한 텍스트 값을 설정하십시오.
1. 범위를 보조 저장소 보기로 변경하고 속성을 다른 값으로 업데이트합니다.
1. 범위를 기본 스토어 보기 및 보조 스토어 보기로 변경한 다음 제품 가시성을 *개별적으로 표시되지 않음*(으)로 설정하십시오.
1. **[!UICONTROL System]** > **[!UICONTROL Export]**(으)로 이동한 다음 드롭다운 메뉴에서 *제품*&#x200B;을(를) 선택합니다.
1. 필터를 설정합니다. 여기서 **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]*&#x200B;이고 **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.
1. 다음 명령을 실행하여 내보내기를 처리합니다.

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. 내보낸 파일을 확인합니다.

<u>예상 결과</u>:

필터링된 레코드만 내보냅니다.

<u>실제 결과</u>:

내보낸 파일에는 내보내는 동안 설정된 필터 기준과 일치하지 않는 보조 스토어 보기에 대한 행이 포함되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
