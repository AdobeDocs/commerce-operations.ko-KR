---
title: 'ACSD-62591: [!UICONTROL User Agent Rules]을(를) 구성할 ** 테마가 전환되지 **'
description: ACSD-62591 패치를 적용하여 **[!UICONTROL User Agent Rules]**이(가) 구성되었을 때 테마가 제대로 전환되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Themes
role: Admin, Developer
source-git-commit: 319ac7ea1fb8f33f4ed7bfa440477cf6d6657cb5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# ACSD-62591: [!UICONTROL User Agent Rules]을(를) 구성할 때 테마가 제대로 전환되지 않습니다.

ACSD-62591 패치를 사용하면 **[!UICONTROL User Agent Rules]**&#x200B;이(가) 구성될 때 테마가 제대로 전환되지 않는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62591입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL User Agent Rules]**&#x200B;이(가) 구성된 경우 테마가 제대로 전환되지 않습니다.

<u>재현 단계</u>:

1. Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**&#x200B;을(를) 엽니다.
1. 스토어 보기 테마를 편집합니다.
1. **[!UICONTROL User Agent Rules]**&#x200B;에서 `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i`을(를) 설정하고 다른 테마를 선택하세요.
1. 변경 사항을 저장하고 캐시를 지웁니다.
1. 모바일 장치에서 Storefront 페이지를 엽니다.
1. 데스크탑 브라우저에서 동일한 페이지를 엽니다.

<u>예상 결과</u>:

데스크탑 브라우저와 모바일 디바이스는 각각의 테마를 사용하여 페이지를 표시한다.

<u>실제 결과</u>:

데스크탑 브라우저에는 모바일 테마와 함께 캐시된 페이지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
