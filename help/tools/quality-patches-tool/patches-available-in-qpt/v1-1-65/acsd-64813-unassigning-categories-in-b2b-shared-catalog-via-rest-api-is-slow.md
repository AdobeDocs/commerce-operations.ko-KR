---
title: 'ACSD-64813: REST API를 통해  [!DNL B2B] 공유 카탈로그에서 범주 할당을 취소하는 데 시간이 오래 걸립니다.'
description: REST API를 통해  [!DNL B2B] 공유 카탈로그에서 범주 할당 취소가 느려지는 Adobe Commerce 문제를 해결하려면 ACSD-64813 패치를 적용합니다.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0ed4bde6d78429da5a375a8c50f6b348db5a5ad5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-64813: REST API를 통해 [!DNL B2B] 공유 카탈로그에서 범주 할당을 취소하는 데 시간이 오래 걸립니다.

ACSD-64813 패치는 REST API를 통해 [!DNL B2B] 공유 카탈로그의 범주 할당 취소가 느려지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-64813입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API를 통해 [!DNL B2B] 공유 카탈로그에서 범주 할당을 취소하는 데 속도가 느립니다.

<u>재현 단계</u>:

1. **[!UICONTROL B2B]**, **[!UICONTROL Company]** 및 **[!UICONTROL Shared Catalog]**&#x200B;을(를) 사용하도록 설정합니다.
1. 30,000개의 활성 재고 제품을 생성합니다.
1. [사용자 지정 공유 카탈로그](https://experienceleague.adobe.com/ko/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls)를 만들고 모든 제품을 할당합니다.
1. 기본 루트 범주 아래에 새 범주를 만들고 몇 가지 제품을 할당합니다.
1. 관리 토큰을 사용하여 새 범주 ID로 REST API 끝점 `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories`을(를) 호출하십시오.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

1. 응답이 *true*&#x200B;인지 확인하십시오.
1. `bin/magento cron:run`을(를) 두 번 실행하거나 다시 색인화하십시오.
1. 관리 토큰을 사용하여 새 범주 ID로 REST API 끝점 `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories`을(를) 호출하십시오.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

<u>예상 결과</u>:

이 작업은 적절한 시간(2~3분 이내) 내에 완료되어야 합니다.

<u>실제 결과</u>:

실행에는 약 30분이 소요되거나 시간 초과 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
