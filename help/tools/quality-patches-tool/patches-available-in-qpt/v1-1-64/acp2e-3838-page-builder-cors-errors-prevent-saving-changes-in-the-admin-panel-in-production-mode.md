---
title: 'ACP2E-3838: [!DNL Page Builder] CORS 오류로 인해 프로덕션 모드의 관리 패널에서 변경 사항이 저장되지 않습니다.'
description: ACP2E-3838 패치를 적용하여  [!DNL Page Builder] CORS 오류로 인해 프로덕션 모드의 관리 패널에 변경 사항이 저장되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACP2E-3838: [!DNL Page Builder] CORS 오류로 인해 프로덕션 모드의 관리 패널에서 변경 사항이 저장되지 않습니다.

ACP2E-3838 패치는 [!DNL Page Builder] CORS 오류로 인해 프로덕션 모드의 관리 패널에서 변경 사항이 저장되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACP2E-3838입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Page Builder]개의 CORS 오류로 인해 프로덕션 모드에서 관리 패널의 변경 내용을 저장할 수 없습니다.

<u>재현 단계</u>:

1. 관리 패널에 로그인합니다.
1. **[!UICONTROL Content]** > **[!UICONTROL Pages]**(으)로 이동합니다.
1. **[!UICONTROL Add New Page]**&#x200B;을(를) 클릭하거나 기존 CMS 페이지를 선택하고 **[!UICONTROL Edit]**&#x200B;을(를) 클릭합니다.
1. 새 콘텐츠 블록을 추가하거나 기존 블록을 편집하려면 **[!UICONTROL Edit with Page Builder]**&#x200B;을(를) 클릭하십시오.
1. 텍스트, 이미지 또는 기타 요소 추가와 같이 콘텐츠를 변경합니다.
1. **[!UICONTROL Save]** 단추를 클릭합니다.

<u>예상 결과</u>:

페이지 콘텐츠가 오류 없이 성공적으로 저장되어야 합니다.

<u>실제 결과</u>:

1. [!DNL Page Builder] 변경 내용을 저장하지 못했습니다.
1. 브라우저 콘솔은 CORS 관련 오류를 기록합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
