---
title: 'ACSD-62415: Adobe Commerce 백엔드가 [!UICONTROL Categories]을(를) 매우 느리게 로드합니다.'
description: ACSD-62415 패치를 적용하여 많은 앵커 범주가 있는 경우 [!UICONTROL Categories] 패널의 [!UICONTROL Admin] 페이지 성능이 매우 느리게 로드되는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415: 앵커 범주가 있는 경우 Adobe Commerce 백엔드가 **[!UICONTROL Categories]**&#x200B;을(를) 매우 느리게 로드합니다.

ACSD-62415 패치는 앵커 범주가 많으면 **[!UICONTROL Categories]** 패널의 **[!UICONTROL Admin]** 페이지 성능이 매우 느리게 로드되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62415입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

앵커 범주가 많으면 **[!UICONTROL Categories]** 패널의 **[!UICONTROL Admin]** 페이지가 매우 느리게 로드됩니다.

<u>재현 단계</u>:

1. 3K 앵커 카테고리를 생성합니다.
1. **[!UICONTROL Catalog]** 패널에서 **[!UICONTROL Categories]** > **[!UICONTROL Admin]** 페이지를 엽니다.

<u>예상 결과</u>:

**[!UICONTROL Categories]** 페이지가 빠르게 로드되며 쿼리를 1K번 반복하면 안 됩니다.

<u>실제 결과</u>:

로드하는 데 7~20초가 걸리고 쿼리가 1K번 이상 실행됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
