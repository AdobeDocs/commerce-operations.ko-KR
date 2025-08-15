---
title: 'MDVA-42689: 가져오는 동안 제품 카테고리를 업데이트하는 동안 사용자가 무결성 제약 조건 위반 오류를 표시함'
description: MDVA-42689 패치는 가져오는 동안 제품 범주를 업데이트하는 동안 사용자가 무결성 제약 조건 위반 오류를 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42689입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: 3f81f195-5a95-45f6-8970-403b8398e759
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-42689: 가져오는 동안 제품 카테고리를 업데이트하는 동안 사용자가 무결성 제약 조건 위반 오류를 표시함

MDVA-42689 패치는 가져오는 동안 제품 범주를 업데이트하는 동안 사용자가 무결성 제약 조건 위반 오류를 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42689입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Adobe Commerce은 가져오는 동안 제품 카테고리를 업데이트하는 동안 무결성 제한 위반 오류를 발생시킵니다.

<u>재현 단계</u>:

1. 두 개의 웹 사이트를 설정합니다.
1. 카테고리 페이지의 최대 두 수준까지 루트 카테고리 아래에 하위 카테고리를 만듭니다. 예를 들어, 루트 범주 > **톱니바퀴** > **시계**&#x200B;입니다.
1. 두 개의 간단한 제품을 만들고 두 제품을 동일한 **톱니바퀴** > **시계** 범주에 할당합니다.
1. 두 웹 사이트 모두에 하나의 간단한 제품을 할당합니다.
1. 제품을 저장합니다.
1. 가져올 CSV 파일을 준비합니다. 스토어 조회수가 다른 제품 레코드가 두 개 있어야 합니다. 제품 중 하나가 이러한 스토어 조회수 모두에 속해야 합니다.
1. 이제 **시스템** > **가져오기** > **엔터티 형식**(제품)으로 이동하여 CSV 파일을 가져옵니다.

<u>예상 결과</u>:

CSV 파일을 오류 없이 가져옵니다.

<u>실제 결과</u>:

Adobe Commerce에서 다음 오류가 발생합니다.

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
