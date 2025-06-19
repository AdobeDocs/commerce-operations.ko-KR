---
title: 'ACSD-63793: 가져오기 프로세스가 서로 다른 브라우저 탭에서 서로 간섭합니다.'
description: ACSD-63793 패치를 적용하여 가져오기 프로세스가 서로 다른 브라우저 탭에서 서로 간섭하는 Adobe Commerce 문제를 수정합니다.
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-63793: 가져오기 프로세스가 서로 다른 브라우저 탭에서 서로 간섭합니다.

ACSD-63793 패치는 가져오기 프로세스가 서로 다른 브라우저 탭에서 상호 간섭하는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63793입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리 UI를 통해 데이터를 가져오면 다른 가져오기가 방해되어 한 가져오기의 데이터가 다른 가져오기에서 처리됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**(으)로 이동합니다.
1. **[!UICONTROL Entity Type]**&#x200B;을(를) *[!UICONTROL Customers and Addresses](단일 파일)*(으)로 설정합니다.
1. **[!UICONTROL Import Behavior]**&#x200B;을(를) *[!UICONTROL Add/Update]*(으)로 설정합니다.
1. 가져올 올바른 파일을 선택하십시오.
1. **[!UICONTROL Check Data]** 단추를 클릭합니다.
1. 이 탭을 열어 두십시오.
1. 새 탭을 열고 잘못된 데이터가 포함된 파일로 단계를 반복합니다(예: 다른 고객을 위한 두 개의 동일한 이메일).
1. 첫 번째 탭으로 다시 전환합니다.
1. 맨 아래에 있는 **[!UICONTROL Import]** 단추를 클릭합니다.

<u>예상 결과</u>:

가져오기 프로세스는 서로 간섭해서는 안 됩니다.

<u>실제 결과</u>:

가져오기 프로세스가 완료되고 보고서 파일을 다운로드할 수 있습니다. 두 번째 행에 오류가 있으며, 초기 유효성 검사가 오류 없이 통과되었더라도 다른 가져오기의 데이터가 처리됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
