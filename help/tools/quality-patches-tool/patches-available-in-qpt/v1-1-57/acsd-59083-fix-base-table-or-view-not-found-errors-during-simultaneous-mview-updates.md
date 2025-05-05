---
title: 'ACSD-59083: 동시 mview 업데이트 중 기본 테이블 또는 뷰에 오류가 없음'
description: ACSD-59083 패치를 적용하여 '기본 테이블 또는 뷰를 찾을 수 없음' 오류와 함께 특정 데이터베이스 업데이트 작업이 실패하는 Adobe Commerce 문제를 해결합니다.
feature: System
role: Admin, Developer
source-git-commit: 7f091ff8db7973c4290e0412d19e9088f1220cef
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-59083: `mview`개의 동시 업데이트 중 *기본 테이블 또는 뷰를 찾을 수 없음* 오류

ACSD-59083 패치는 `mview` 업데이트가 동시에 실행될 때 &#39;기본 테이블 또는 보기를 찾을 수 없음&#39; 오류와 함께 특정 데이터베이스 업데이트 작업이 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-59083입니다. 이 문제는 Adobe Commerce 2.4.8에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`mview` 업데이트가 동시에 실행될 때 특정 데이터베이스 업데이트 작업으로 인해 &#39;기본 테이블 또는 뷰를 찾을 수 없음&#39; 오류가 발생합니다.

<u>재현 단계</u>:

1. 인덱서 모드를 **[!UICONTROL Update on Schedule]**(으)로 설정합니다.
1. 다음 SQL 명령을 사용하여 `cl` 테이블에 레코드를 삽입합니다.

   ```
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. `setup/performance-toolkit/profiles/ce/small.xml` 프로필을 설치합니다.
1. `magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php` 파일의 72행에 중단점을 추가합니다.
1. 캐시를 지웁니다.
1. 제품에서 **[!UICONTROL Add to Cart]**&#x200B;을(를) 클릭합니다.
1. 실행이 중단점에 도달하면 크론 작업을 시작합니다.
1. cron 작업을 시작한 후 프로세스를 재개합니다.

<u>예상 결과</u>:

데이터베이스 작업이 오류 없이 성공적으로 실행됩니다.

<u>실제 결과</u>:

실행 도중 오류 발생:

```
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
