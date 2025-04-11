---
title: 'ACP2E-3705: ''MAGE_INDEXER_THREADS_COUNT''가 설정되면 ''indexer_update_all_views'' cron 실행이 실패합니다'
description: '''MAGE_INDEXER_THREADS_COUNT''가 설정되면 ''indexer_update_all_views'' cron 실행이 실패하는 Adobe Commerce 문제를 해결하려면 ACP2E-3705 패치를 적용합니다.'
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
source-git-commit: 7ef772510274bc8681c395656437d64f8b40e70a
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705: `MAGE_INDEXER_THREADS_COUNT`이(가) 설정되면 `indexer_update_all_views` cron 실행이 실패합니다

>[!NOTE]
>
>이 패치는 버전 2.4.7 이상의 [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)을(를) 대체합니다.

ACP2E-3705 패치는 `MAGE_INDEXER_THREADS_COUNT`이(가) 설정되어 있을 때 `indexer_update_all_views` cron 실행이 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3705입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`MAGE_INDEXER_THREADS_COUNT`이(가) *2*&#x200B;보다 큰 값으로 설정된 경우 `indexer_update_all_views` cron 실행이 실패하며, 특히 B2B가 활성화된 [!UICONTROL Customer Segments] 인덱서에 영향을 줍니다.

<u>재현 단계</u>:

1. QPT 패치 [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)을(를) 적용합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**(으)로 이동합니다.
1. **[!UICONTROL Category Permissions]** 사용
1. 다음 인덱서를 **[!UICONTROL Update on Schedule]** 모드로 설정합니다.

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. 몇 가지 제품을 만들고 카테고리에 할당합니다.
1. 전체 색인 재지정을 실행합니다.
1. 범주로 이동하여 **[!UICONTROL Category Permissions]**&#x200B;을(를) 설정합니다.
1. `MAGE_INDEXER_THREADS_COUNT`이(가) *8*(으)로 설정된 `indexer_update_all_views` cron 작업을 실행합니다.

<u>예상 결과</u>:

색인 재지정이 오류 없이 완료되었습니다.

<u>실제 결과</u>:

`indexer_update_all_views` cron 작업에 다음 오류가 발생했습니다.

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
