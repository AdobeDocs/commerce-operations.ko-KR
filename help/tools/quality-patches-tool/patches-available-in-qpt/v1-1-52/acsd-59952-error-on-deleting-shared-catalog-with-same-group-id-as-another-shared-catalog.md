---
title: 'ACSD-59952: 다른 공유 카탈로그와 동일한 그룹 ID를 사용하는 공유 카탈로그를 삭제하는 도중 오류 발생'
description: ACSD-59952 패치를 적용하여 다른 공유 카탈로그와 동일한 'customer_group_id'가 있는 공유 카탈로그를 삭제할 때 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952: 다른 공유 카탈로그와 동일한 그룹 ID를 사용하는 공유 카탈로그를 삭제하는 도중 오류 발생

ACSD-59952 패치는 다른 공유 카탈로그와 동일한 `customer_group_id`의 공유 카탈로그를 삭제할 때 발생하는 오류를 수정합니다. 또한 사용자가 이러한 공유 카탈로그를 만들 수 없습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-59952입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다른 공유 카탈로그와 동일한 `customer_group_id`을(를) 가진 새 공유 카탈로그를 만들 수 없습니다. 그러나 이 경우 동일한 `customer_group_id`을(를) 사용하여 공유 카탈로그를 삭제하려고 하면 오류가 발생합니다.

<u>필수 구성 요소</u>:

Adobe Commerce B2B 모듈을 설치합니다.

<u>재현 단계</u>:

1. 다음 REST API 호출을 사용하여 동일한 `customer_group_id`에 할당된 여러 공유 카탈로그를 만드십시오.

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. 다음 REST API 호출을 사용하여 공유 카탈로그를 삭제해 보십시오.

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>예상 결과</u>:

* 동일한 `customer_group_id`에 할당된 공유 카탈로그를 여러 개 만들 수 없습니다.
* 위의 경우 공유 카탈로그가 삭제되었습니다.

<u>실제 결과</u>:

* 동일한 `customer_group_id`에 할당된 공유 카탈로그를 여러 개 만들 수 있습니다.
* 동일한 `customer_group_id`의 공유 카탈로그를 삭제하려고 할 때 다음 오류가 반환됩니다. *공유 카탈로그를 삭제할 수 없습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
