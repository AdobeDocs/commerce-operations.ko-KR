---
title: 'ACSD-64112: ''MAGE_INDEXER_THREADS_COUNT''가 설정되면 ''indexer_update_all_views'' cron 실행이 실패합니다'
description: ACSD-64112 패치를 적용하여 'MAGE_INDEXER_THREADS_COUNT'가 설정되면 'indexer_update_all_views' cron 실행이 실패하는 Adobe Commerce 문제를 수정합니다.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112: `indexer_update_all_views`이(가) 설정되면 `MAGE_INDEXER_THREADS_COUNT` cron 실행이 실패합니다.

>[!NOTE]
>
>이 패치는 2.4.7 이상 버전의 Adobe Commerce용 [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md)(으)로 대체되었습니다.

ACSD-64112 패치는 `indexer_update_all_views`이(가) 설정되면 `MAGE_INDEXER_THREADS_COUNT` cron 실행이 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64112입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p10

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`indexer_update_all_views`이(가) 2보다 큰 값으로 설정되어 있으면 `MAGE_INDEXER_THREADS_COUNT` cron 실행이 실패합니다. 특히 B2B가 활성화된 [!UICONTROL Customer Segments] 인덱서에 영향을 줍니다.

<u>재현 단계</u>:

1. B2B를 사용하여 깨끗한 인스턴스를 설치합니다.
1. **[!UICONTROL B2B Company]** 및 **[!UICONTROL Shared Catalog]**&#x200B;을(를) 사용하도록 설정합니다.
1. 카테고리를 만듭니다.
1. 몇 가지 제품을 만들고 카테고리에 할당합니다.
1. 전체 색인 재지정을 실행합니다.
1. 다음 인덱서를 **[!UICONTROL Update on Schedule]**(으)로 설정합니다.

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. 백엔드로 이동하여 새로 생성된 카테고리를 로드합니다.
1. **[!UICONTROL Category Permissions]**&#x200B;을(를) 클릭하고 기존 고객 그룹에 대해 **[!UICONTROL New Permission]**&#x200B;을(를) 만듭니다.
1. `catalogpermissions_category` 인덱서에 백로그가 있는지 확인하십시오. 다음 명령을 실행하여 확인합니다.

   ```
   bin/magento indexer:status
   ```

1. `env.php`에서 다음 인덱서 스레드 수를 설정하십시오.

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. cron 작업 실행:

   ```
   bin/magento cron:run
   ```

<u>예상 결과</u>:

cron 작업은 문제 없이 실행해야 합니다.

<u>실제 결과</u>:

`indexer_update_all_views` cron 작업에 다음 오류가 발생했습니다.

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 패치 설치 후 추가 단계 필요

(이 섹션은 선택 사항입니다. 문제를 해결하기 위해 패치를 적용한 후 몇 가지 단계가 필요할 수 있습니다.) 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
