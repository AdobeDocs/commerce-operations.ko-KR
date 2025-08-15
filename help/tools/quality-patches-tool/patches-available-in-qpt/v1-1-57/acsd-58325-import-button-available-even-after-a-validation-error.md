---
title: 'ACSD-58325: 유효성 검사 오류 후에도 [!UICONTROL Import] 단추를 사용할 수 있음'
description: ACSD-58325 패치를 적용하여 유효성 검사 오류 후에도 [!UICONTROL Import] 단추를 사용할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325: 유효성 검사 오류 후에도 [!UICONTROL Import] 단추를 사용할 수 있음

ACSD-58325 패치는 유효성 검사 오류 후에도 **[!UICONTROL Import]** 단추를 사용할 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58325입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

유효성 검사 오류가 발생한 후에도 [!UICONTROL Import] 단추를 사용할 수 있습니다.

<u>재현 단계</u>:

1. 파일에 잘못된 이미지 이름이 있는 제품 가져오기용 CSV 파일을 만듭니다.
1. 생성된 CSV 파일을 사용하여 예약된 제품 가져오기를 만듭니다.
1. 예약된 가져오기가 수행될 때까지 기다립니다.
1. [!UICONTROL Last outcome] 눈금의 **[!UICONTROL Scheduled Imports/Exports]**&#x200B;을(를) 확인합니다.

<u>예상 결과</u>:

[!UICONTROL Last outcome]은(는) [!UICONTROL Failed]이어야 합니다.

<u>실제 결과</u>:

[!UICONTROL Last outcome]은(는) [!UICONTROL Successful]입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
