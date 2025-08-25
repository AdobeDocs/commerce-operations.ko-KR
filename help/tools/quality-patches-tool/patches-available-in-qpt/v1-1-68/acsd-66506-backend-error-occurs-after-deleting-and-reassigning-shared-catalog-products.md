---
title: 'ACSD-66506: 공유 카탈로그 제품을 삭제하고 재할당한 후 백엔드 오류가 발생합니다'
description: ACSD-66506 패치를 적용하여 백엔드에서 오류가 발생하는 Adobe Commerce 문제를 해결합니다 *요청된 제품이 존재하지 않습니다. 이전에 할당한 제품을 삭제하고 새 제품을 공유 카탈로그에 할당한 후 제품을 확인하고 다시 시도하십시오*.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506: 공유 카탈로그 제품을 삭제하고 재할당한 후 백엔드 오류가 발생합니다

ACSD-66506 패치가 백엔드에서 오류 *이(가) 발생하는 문제를 해결했습니다. 요청한 제품이 없습니다. 이전에 할당된 제품을 삭제하고 새 제품을 공유 카탈로그에 할당한 후 제품을 확인하고*&#x200B;을(를) 다시 시도하십시오. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66506입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이전에 할당된 제품을 삭제하고 새 제품을 **[!UICONTROL Shared Catalog]**&#x200B;에 할당하면 백엔드에서 다음 오류를 반환합니다. *요청한 제품이 없습니다. 제품을 확인하고 다시 시도하십시오.*

<u>재현 단계</u>:

1. 성능 도구 키트를 사용하여 일부 제품 만들기: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. **[!UICONTROL [!DNL B2B] Features]** 구성으로 이동한 다음 **[!UICONTROL Enable Company]** 및 **[!UICONTROL Enable Shared Catalog]**&#x200B;을(를) `Yes`(으)로 설정합니다.
1. 새 공유 카탈로그를 만듭니다.
1. 생성된 모든 제품을 새로 생성된 공유 카탈로그에 할당합니다.
1. **[!UICONTROL Product Import]**&#x200B;을(를) 사용하여 공유 카탈로그에 할당된 제품을 삭제하십시오.
   1. SKU로 필터링된 제품 내보내기
   1. **[!UICONTROL Import Behavior: Delete]**&#x200B;을(를) 선택한 다음 동일한 파일을 가져옵니다.
1. **[!UICONTROL Shared Catalog]**&#x200B;을(를) 열고 가격 및 구조를 구성합니다.
   1. **[!UICONTROL Set Pricing and Structure]**&#x200B;을(를) 선택합니다.
   1. **[!UICONTROL Next]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Generate Catalog]**&#x200B;을(를) 클릭합니다.
   1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

오류가 발생하지 않으며 오류가 발생하더라도 제품이 공유 카탈로그에 남아 있습니다.

<u>실제 결과</u>:

오류가 발생했습니다. *요청한 제품이 없습니다. 제품을 확인하고*&#x200B;을(를) 다시 시도하세요. 그러면 모든 제품이 공유 카탈로그에서 제거됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
