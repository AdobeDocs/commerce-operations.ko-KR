---
title: 'ACSD-62635:  [!DNL GraphQL]에 다중 스토어 관련 제품이 잘못 표시됨'
description: ACSD-62635 패치를 적용하여 다중 스토어 관련 제품이  [!DNL GraphQL] 제품 쿼리에 제대로 표시되지 않는 Adobe Commerce 문제를 해결합니다.
feature: B2B
role: Admin, Developer
source-git-commit: 8e6f6590dbed43eb8ce75b694a05ee951b538814
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635: [!DNL GraphQL]에 다중 스토어 관련 제품이 잘못 표시됨

ACSD-62635 패치를 사용하면 다중 스토어 관련 제품이 [!DNL GraphQL] 제품 쿼리에 제대로 표시되지 않는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62635입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

B2B가 활성화되면 [!DNL GraphQL] 요청은 스토어 보기 범위가 요청에 사용된 경우에도 모든 웹 사이트에서 모든 관련 제품을 반환합니다.

<u>재현 단계</u>:

1. 두 개의 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 다음과 같은 간단한 제품을 만듭니다.
   * 모든 웹 사이트에 SKU *product1*&#x200B;이(가) 할당된 기본 항목 1개
   * *웹 사이트 1*&#x200B;에만 할당된 항목 1개
   * *웹 사이트 2*&#x200B;에만 할당된 항목 1개
   * *웹 사이트 1* 및 *웹 사이트 2* 모두에 할당된 1개
1. *product1*&#x200B;과(와) 관련된 모든 제품을 추가하십시오.
1. [!UICONTROL B2B] 및 [!UICONTROL Shared Catalog]을(를) 사용하도록 설정합니다.
1. 기본 공유 카탈로그에 모든 제품을 추가합니다.
1. 헤더에서 *웹 사이트 1*&#x200B;의 스토어 코드로 *product1* 및 관련 제품을 검색하도록 [!DNL GraphQL] 요청을 보냅니다.

<u>예상 결과</u>:

응답에는 요청 헤더에 전송된 스토어 코드에 해당하는 웹 사이트의 관련 제품만 포함됩니다.

<u>실제 결과</u>:

응답에는 요청에 지정된 스토어 코드에 관계없이 모든 웹 사이트의 모든 관련 제품이 포함됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
