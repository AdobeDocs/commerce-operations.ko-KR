---
title: 'ACSD-47054: 모든 스토어가 다시 인덱싱하므로 콘텐츠 미리보기 속도가 느림'
description: ACSD-47054 패치를 적용하여 모든 스토어의 색인 재지정으로 인해 미리보기 페이지가 느리게 로드되는 Adobe Commerce 문제를 해결합니다.
feature: Page Content
role: Admin, Developer
exl-id: bfbda95a-354b-4b67-8081-84aefbbd7cb4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47054: 모든 스토어가 다시 인덱싱하므로 콘텐츠 미리보기 속도가 느림

ACSD-47054 패치는 저장소가 많을 때 콘텐츠 스테이징 미리보기를 로드하는 데 시간이 더 오래 걸리는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47054입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법): 2.4.2-p2, 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

모든 스토어의 색인 재지정으로 인해 미리보기 페이지를 로드하는 데 시간이 오래 걸립니다.

<u>재현 단계</u>:

1. Commerce 관리자로 이동합니다.
1. 예약된 업데이트를 만듭니다.
1. **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**(으)로 이동합니다.
1. 예약된 업데이트를 미리 봅니다.
1. 모든 카테고리를 엽니다.

<u>예상 결과</u>:

미리보기 페이지는 일정 시간 내에 로드됩니다.

<u>실제 결과</u>:

콘텐츠 스테이징의 미리 보기에 시간이 오래 걸립니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
