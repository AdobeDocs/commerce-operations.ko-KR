---
title: 'ACSD-58375: YouTube API 키가 잘못 구성되면 스토어 보기 수준에서 비디오를 추가할 때 오류가 발생합니다'
description: ACSD-58375 패치를 적용하여 스토어 보기 수준에서 YouTube 비디오를 추가할 때 잘못된 YouTube API 키 구성으로 인해 오류가 발생하는 Adobe Commerce 문제를 수정합니다.
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-58735: YouTube API 키가 잘못 구성되면 스토어 보기 수준에서 비디오를 추가할 때 오류가 발생합니다

ACSD-58735 패치는 스토어 보기 수준에서 YouTube 비디오를 추가할 때 잘못된 YouTube API 키 구성으로 인해 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58735입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

잘못된 YouTube API 키 구성으로 인해 스토어 보기 수준에서 YouTube 비디오를 추가할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. 관리자 > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**(으)로 이동합니다.
1. *범위*&#x200B;을(를) *[!UICONTROL Main Website]* 수준으로 변경합니다.
1. YouTube API 키를 추가합니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동합니다.
1. 제품을 선택하고 *[!UICONTROL Images and Video]*(으)로 스크롤합니다. **[!UICONTROL Add Video]**&#x200B;을(를) 클릭합니다.
1. YouTube 비디오 링크를 복사하여 비디오 링크 필드에 붙여넣습니다. 필드에서 나가세요.

<u>예상 결과</u>:

YouTube API 키는 전역 범위를 포함하며 웹 사이트 수준에서 숨겨집니다.

<u>실제 결과</u>:

다음 오류가 발생했습니다. *API 키가 잘못되었기 때문에 비디오가 표시되지 않습니다. 올바른 API 키*&#x200B;을(를) 전달하십시오.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
