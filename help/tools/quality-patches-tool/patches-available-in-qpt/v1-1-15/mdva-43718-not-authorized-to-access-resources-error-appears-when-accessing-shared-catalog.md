---
title: 'MDVA-43718: 공유 카탈로그에 액세스할 때 ''소비자가 리소스에 액세스할 권한이 없습니다.'' 오류가 표시됩니다.'
description: MDVA-43718 패치를 사용하면 *소비자가 %resources에 액세스할 수 있는 권한이 없는 문제가 해결됩니다.* 사용자 정의 통합에서 공유 카탈로그에 액세스할 때 표시됩니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43718입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Catalog Management
role: Admin
exl-id: 2ced2177-aeff-4c36-8d34-6028539b66bd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-43718: 공유 카탈로그에 액세스할 때 &#39;소비자가 리소스에 액세스할 권한이 없습니다.&#39; 오류가 표시됩니다.

MDVA-43718 패치를 사용하면 오류 *소비자가 %resources에 액세스할 수 있는 권한이 없는 문제가 해결됩니다.사용자 지정 통합에서 공유 카탈로그에 액세스할 때*&#x200B;이(가) 나타납니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43718입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 통합에서 공유 카탈로그에 액세스할 때 다음 오류가 나타납니다. *소비자가 %resources에 액세스할 권한이 없습니다*.

<u>재현 단계</u>:

1. 관리자 > **시스템** > **통합** > **통합 추가**&#x200B;에서 새 통합을 만듭니다.
1. 다음 리소스에 대한 액세스 권한을 추가하고 통합을 활성화합니다.

   * Magento_SharedCatalog::list
   * Magento_공유 카탈로그::manage
   * Magento 카탈로그::catalog

1. 통합 액세스 사용: `rest/default/V1/sharedCatalog/1`

<u>예상 결과</u>:

공유 카탈로그의 세부 사항이 반환됩니다.

<u>실제 결과</u>:

다음 오류가 반환됩니다.

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
