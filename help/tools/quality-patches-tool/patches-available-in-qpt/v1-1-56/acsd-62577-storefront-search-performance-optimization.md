---
title: 'ACSD-62577: 상점 검색 성능 최적화'
description: ACSD-62577 패치를 적용하여 큰 'search_query' 테이블로 인해 쿼리 실행이 느려져 상점 검색 성능이 저하되는 Adobe Commerce 문제를 해결합니다.
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577: 상점 검색 성능 최적화

ACSD-62577 패치는 쿼리 및 테이블 인덱스를 최적화하여 상점 검색 쿼리의 성능이 저하되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56에서 사용할 수 있습니다. 패치 ID는 ACSD-62577입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6, 2.4.7-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

큰 `search_query` 테이블은 상점 검색 속도를 크게 늦추므로 비효율적인 쿼리와 최적화된 테이블 인덱스의 부족으로 인해 프론트엔드 응답 시간이 늘어납니다.

<u>재현 단계</u>:

1. 성능 도구 키트 `small.xml`을(를) 사용하여 Adobe Commerce Develop을 설정합니다.
1. 다음 명령을 사용하여 SQL 명령줄에 액세스하고 `search_query` 테이블을 삭제합니다.

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. `search_query` 테이블을 많은 레코드(예: 4백만 개 레코드)로 채웁니다.
1. 리인덱싱을 트리거하고 캐시를 플러시합니다.

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. 데이터베이스 디버그 로그 활성화:

   ```
   bin/magento dev:query-log:enable  
   ```

1. 상점 검색 창에서 검색어(예:
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. 다음 SQL의 쿼리 실행 시간에 대한 `db.log`을(를) 확인하십시오.

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>예상 결과</u>:

쿼리 실행 시간이 최적화되어 대형 `search_query`개 테이블을 처리할 때 응답 시간이 크게 증가하지 않습니다.

<u>실제 결과</u>:

큰 `search_query` 테이블의 비효율적인 처리로 인해 쿼리 실행 시간이 크게 증가합니다.

```
TIME: 10.8520 seconds  
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
