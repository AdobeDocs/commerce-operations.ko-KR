---
title: 'ACSD-49065: 관리자에 견적 항목이 표시되지 않음'
description: ACSD-49065 패치를 적용하여 견적 항목이 사용자 지정 재고에만 할당된 경우 관리자에 표시되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: 관리자에 견적 항목이 표시되지 않음

ACSD-49065 패치는 견적 항목이 사용자 지정 재고에만 할당된 경우 관리자에 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49065입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

견적 항목이 사용자 지정 주식에만 할당된 경우 관리자에 표시되지 않습니다.

사전 요구 사항:

**[!UICONTROL B2B]** 및 **[!UICONTROL Inventory]** 모듈이 설치되어 있어야 합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Company]** > **[!UICONTROL B2B Quote]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]**&#x200B;에서 **[!UICONTROL General]** 및 **[!UICONTROL B2B Features]**&#x200B;을(를) 활성화합니다.
1. 보조 **[!UICONTROL Inventory Source]**&#x200B;을(를) 만들어 보조 **[!UICONTROL Inventory Stock]**&#x200B;에 할당합니다.
1. 기본값이 아닌 보조 **[!UICONTROL Inventory Source]**&#x200B;만 할당하여 새 제품을 만드십시오.
1. 상점으로 이동하여 새 회사 계정을 만듭니다. **[!UICONTROL Company Admin]**(으)로 로그인하고 만든 제품을 장바구니에 추가합니다.
1. 장바구니 및 *[!UICONTROL Request a Quote]*(으)로 이동합니다.
1. 책임자로 이동하여 **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;에서 요청된 견적을 확인하십시오.

<u>예상 결과</u>:

항목은 제품을 다시 저장하지 않고 새 제품으로 생성된 새 견적에 표시됩니다.

<u>실제 결과</u>:

*[!UICONTROL Items Quoted]* 섹션이 비어 있습니다. 새로 만든 제품을 다시 저장하면 항목이 나타납니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
