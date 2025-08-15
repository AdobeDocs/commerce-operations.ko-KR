---
title: 'MDVA-43601: 트리거는 전체 색인 재지정 후 "catalogrule_product_price" 테이블에서 제거됩니다.'
description: MDVA-43601 패치는 'catalogrule_rule' 또는 'catalogrule_product'의 전체 색인 변경 후 트리거가 'catalogrule_product_price' 테이블에서 제거되는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43601입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-43601: 트리거는 전체 색인 재지정 후 &quot;catalogrule_product_price&quot; 테이블에서 제거됩니다.

MDVA-43601 패치는 `catalogrule_product_price` 또는 `catalogrule_rule`을(를) 전체 다시 인덱싱한 후 `catalogrule_product` 테이블에서 트리거가 제거되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43601입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`catalogrule_product_price` 또는 `catalogrule_rule`을(를) 완전히 다시 인덱싱한 후 `catalogrule_product` 테이블에서 트리거가 제거됩니다.

<u>재현 단계</u>:

1. 모든 인덱서를 *일정별 업데이트*(으)로 설정하십시오.
1. 다음 SQL 요청을 실행하여 `catalogrule_product_price` 테이블에 대해 만들어진 트리거를 확인하십시오.

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. 다음 명령을 실행하여 `catalogrule_rule` 또는 `catalogrule_product`을(를) 수동으로 다시 인덱싱합니다. `bin/magento indexer:reindex catalogrule_rule`
1. `catalogrule_product_price` 테이블의 트리거를 다시 확인하십시오.

<u>예상 결과</u>:

`catalogrule_product_price` 테이블의 트리거는 전체 색인 재지정 후 유지됩니다.

<u>실제 결과</u>:

`catalogrule_product_price` 테이블에 대한 트리거가 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
