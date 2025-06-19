---
title: 'ACSD-63286: 공유 카탈로그에 할당된 제품을 표시하려면 수동으로 리인덱싱해야 함'
description: ACSD-63286 패치를 적용하여 API를 통해 공유 카탈로그에 할당된 제품이 수동 색인 재지정이 실행될 때까지 상점 앞에 표시되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286: 공유 카탈로그에 할당된 제품을 표시하려면 수동으로 리인덱싱해야 함

ACSD-63286 패치는 API를 통해 공유 카탈로그에 할당된 제품이 수동 색인 재지정을 실행할 때까지 상점 앞에 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63286입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 API를 통해 공유 카탈로그에 할당되면 부분 인덱서 및 소비자 cron 작업이 실행된 후 프론트엔드에 표시되지 않습니다. 그러나 수동 전체 색인 재지정 후에는 표시됩니다.

<u>재현 단계</u>:

1. [!DNL RabbitMQ]을(를) 큐 서비스로 설정합니다.
1. 공유 카탈로그를 만들고 회사에 할당합니다.
1. 간단한 제품을 만들고 카테고리에 할당합니다.
1. 부분 색인 재지정을 실행합니다.

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 다음 API 요청을 사용하여 만든 제품을 공유 카탈로그 `pub/rest/all/V1/sharedCatalog/<id>/assignProducts`에 지정하십시오.

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 다음 cron을 실행하여 큐를 지우고 부분 리인덱스를 실행합니다.

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 프론트엔드에 회사 사용자로 로그인합니다.
1. 프론트엔드 카테고리 페이지를 확인하십시오. 새로 할당된 제품이 표시되지 않습니다.
1. 수동 색인 재지정 실행:

   ```
   bin/magento index:reindex
   ```

<u>예상 결과</u>:

이 제품은 수동 색인 재지정 없이 프론트엔드에 표시됩니다.

<u>실제 결과</u>:

제품은 수동 색인 재지정 후에만 프런트 엔드에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
