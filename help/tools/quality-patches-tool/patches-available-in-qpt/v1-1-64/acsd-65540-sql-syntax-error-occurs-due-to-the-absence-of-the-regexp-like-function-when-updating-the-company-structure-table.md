---
title: 'ACSD-65540: company_structure 업데이트에 REGEXP_LIKE 함수가 누락되어 SQL 오류가 발생했습니다.'
description: ACSD-65540 패치를 적용하여 company_structure 업데이트에 REGEXP_LIKE 함수가 누락되어 SQL 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# ACSD-65540: `company_structure` 업데이트에 `REGEXP_LIKE` 함수가 누락되어 SQL 오류가 발생했습니다.

ACSD-65540 패치는 `company_structure` 업데이트에서 `REGEXP_LIKE` 함수가 누락되어 SQL 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65540입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce B2B(모든 배포 방법) 1.5.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce B2B(모든 배포 방법) 1.5.2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`company_structure` 업데이트에 `REGEXP_LIKE` 함수가 누락되어 SQL 구문 오류가 발생했습니다.

<u>재현 단계</u>:

1. [!DNL B2B]을(를) 버전 1.5.2로 업데이트합니다.
1. 다음 명령을 실행합니다.

```
bin/magento setup:upgrade
```

<u>예상 결과</u>:

업그레이드가 완료되었습니다.

<u>실제 결과</u>:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
