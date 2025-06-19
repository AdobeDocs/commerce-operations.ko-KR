---
title: 'ACSD-62670: [!UICONTROL Ordered Products Report]을(를) CSV로 내보내고 XML로 내보내면 오류가 발생합니다.'
description: ACSD-62670 패치를 적용하여 [!UICONTROL Ordered Products Report]을(를) CSV 및 XML로 내보내면 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# ACSD-62670: *[!UICONTROL Ordered Products Report]*&#x200B;을(를) CSV로 내보내고 XML로 내보내면 오류가 발생합니다.

ACSD-62670 패치는 *[!UICONTROL Ordered Products Report]*&#x200B;을(를) CSV 및 XML로 내보내면 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62670입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Ordered Products Report]*&#x200B;을(를) CSV 및 XML로 내보내면 오류가 발생합니다.

<u>재현 단계</u>:

1. *관리자* 패널로 이동하여 **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**(으)로 이동합니다.
1. CSV 또는 Excel 파일을 내보내십시오.

<u>예상 결과</u>:

보고서는 오류 없이 내보냅니다.

<u>실제 결과</u>:

*[!UICONTROL Ordered Products Report]*&#x200B;을(를) 내보내면 오류 404가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
