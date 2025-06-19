---
title: 'ACSD-63974: 페이지 매김으로 느린 [!UICONTROL Requisition List] 로드 시간을 수정합니다.'
description: 항목이 너무 많을 때 [!UICONTROL Requisition List] 페이지를 로드하는 데 시간이 오래 걸리는 문제를 해결하려면 ACSD-63974 패치를 적용하세요.
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974: 페이지 매김으로 느린 [!UICONTROL Requisition List] 로드 시간을 수정합니다.

ACSD-63974 패치는 항목이 너무 많을 때 **[!UICONTROL Requisition List]** 페이지를 로드하는 데 시간이 오래 걸리는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63974입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

항목이 많으면 **[!UICONTROL Requisition List]** 페이지를 로드하는 데 시간이 오래 걸립니다(2000+). 페이지 매김이 없기 때문에 모든 항목이 한 번에 로드됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**(으)로 이동합니다.
1. **[!UICONTROL Enable Requisition List]**&#x200B;을(를) *예*(으)로 설정합니다.
1. `setup/performance-toolkit/profiles/ce/small.xml`에서 `simple_products` 노드를 편집하여 2000개 이상의 제품을 생성합니다.
1. 다음 명령을 실행합니다.

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. 고객을 만들고 로그인합니다.
1. **[!UICONTROL Requisition List]**&#x200B;에 모든 제품을 추가합니다.
1. Storefront에서 **[!UICONTROL Requisition List]**&#x200B;을(를) 봅니다.


<u>예상 결과</u>:

적절한 시간 내에 페이지가 로드되어야 합니다.


<u>실제 결과</u>:

페이지 매김이 없기 때문에 모든 항목이 한 번에 로드되기 때문에 페이지 로드 시간이 항목 수에 따라 늘어납니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
