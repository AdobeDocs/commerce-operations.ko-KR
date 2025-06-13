---
title: 'ACSD-57941: 제품 옵션이 관리 저장소에 잘못 할당되었습니다.'
description: ACSD-57941 패치를 적용하여 제품 옵션이 해당 스토어가 아닌 관리 스토어에 잘못 할당되는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: a78c1797-c366-4931-b036-966d3dcf59bb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-57941: 제품 옵션이 관리 저장소에 잘못 할당되었습니다.

ACSD-57941 패치는 제품 옵션이 해당 저장소가 아닌 관리 저장소에 잘못 할당되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57941입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 옵션이 해당 저장소 대신 관리 저장소에 잘못 할당되었습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 몇 가지 사용자 지정 옵션을 사용하여 동일한 제품을 가져옵니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 만든 제품을 엽니다. **[!UICONTROL Customizable options]**&#x200B;을(를) 클릭하고 가져온 옵션이 표시되는지 확인하십시오.
1. 동일한 파일을 몇 번 더 가져옵니다.

<u>예상 결과</u>:

사용자 지정 옵션이 업데이트됩니다.

<u>실제 결과</u>:

제품 사용자 지정 옵션이 중복됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
