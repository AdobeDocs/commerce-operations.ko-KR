---
title: 'ACSD-61103: API를 통해 성공적으로 고객이 로그인한 후 실패 카운트가 0으로 재설정되지 않음'
description: ACSD-61103 패치를 적용하여 고객이 API 끝점을 통해 성공적으로 로그인한 후 'customer_entity' 테이블의 실패 카운트가 0으로 재설정되지 않는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103: API를 통해 성공적으로 고객이 로그인한 후 실패 카운트가 0으로 재설정되지 않음

ACSD-61103 패치는 고객이 API 끝점을 통해 성공적으로 로그인한 후 `customer_entity` 테이블의 오류 수가 0으로 재설정되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61103입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객이 API 끝점을 통해 성공적으로 로그인한 후에도 `customer_entity` 테이블의 오류 수가 0으로 재설정되지 않습니다.

<u>재현 단계</u>:

1. 고객 계정을 만듭니다.
1. 잘못된 세부 정보를 사용하여 API를 통해 고객 토큰을 생성합니다.
1. 위의 고객에 대해 `failures_num` DB 테이블의 `customer_entity` 열을 확인하십시오.
1. 올바른 세부 정보를 사용하여 API를 통해 고객 토큰을 생성합니다.
1. 위의 고객에 대해 `failures_num` DB 테이블의 `customer_entity` 열을 확인하십시오.

<u>예상 결과</u>:

API를 통해 고객 토큰을 생성하기 위해 올바른 자격 증명을 사용한 후 `failures_num` 열을 0으로 다시 설정해야 합니다.

<u>실제 결과</u>:

API를 통해 고객 토큰을 생성하기 위해 올바른 자격 증명을 사용한 후에는 `failures_num` 열이 0으로 재설정되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
