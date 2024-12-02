---
title: 'MDVA-43983: "개별적으로 표시되지 않음"으로 설정된 제품이 검색 결과에 표시됨'
description: MDVA-43983 패치는 "개별적으로 표시되지 않음"으로 설정된 제품이 카탈로그 고급 검색 결과에 여전히 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43983입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983: &quot;개별적으로 표시되지 않음&quot;으로 설정된 제품이 검색 결과에 표시됨

MDVA-43983 패치는 &quot;개별적으로 표시되지 않음&quot;으로 설정된 제품이 카탈로그 고급 검색 결과에 여전히 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43983입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

&quot;개별적으로 표시되지 않음&quot;으로 설정된 제품은 여전히 카탈로그 고급 검색 결과에 표시됩니다.

<u>재현 단계</u>:

1. 저장소 소유자에 대한 **카탈로그 입력 유형**&#x200B;이(가) 있는 특성을 **드롭다운** 또는 **시각적 견본**(예: 색상)으로 만듭니다.
1. **검색에 사용**&#x200B;을 **예**(으)로 설정하고 **고급 검색에 표시**&#x200B;를 **예**(으)로 설정합니다.
1. 일부 속성 옵션을 추가합니다.
1. **개별적으로 표시되지 않음**(으)로 **가시성**&#x200B;을(를) 사용하는 제품을 만드십시오.
1. 색상 속성 옵션을 지정합니다.
1. 상점 첫 화면의 **카탈로그 고급 검색** 페이지로 이동합니다.
1. 색상 속성 필드에서 색상 속성 옵션만 선택하고 나머지 필드는 그대로 또는 비워 둡니다.
1. 고급 검색 양식을 제출합니다.
1. 검색 결과를 확인합니다.

<u>예상 결과</u>:

&quot;개별적으로 표시되지 않음&quot;으로 설정된 제품은 카탈로그 고급 검색 결과에 표시되지 않습니다.

<u>실제 결과</u>:

&quot;개별적으로 표시되지 않음&quot;으로 설정된 제품은 카탈로그 고급 검색 결과에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
