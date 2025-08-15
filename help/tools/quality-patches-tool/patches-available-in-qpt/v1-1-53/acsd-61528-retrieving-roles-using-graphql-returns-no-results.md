---
title: 'ACSD-61528: GraphQL을 사용하여 역할을 검색하면 결과가 반환되지 않음'
description: ACSD-61528 패치를 적용하여 GraphQL을 사용하여 회사 관리자의 역할을 검색하면 항상 null 결과가 반환되는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 81d78746-e723-4b18-860c-d973158b469c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528: GraphQL을 사용하여 역할을 검색하면 결과가 반환되지 않음

ACSD-61258 패치는 GraphQL을 사용하여 회사 관리자의 역할을 검색하면 항상 null 결과가 반환되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61528입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL을 사용하여 회사 관리자의 역할을 검색할 때 역할 결과는 항상 null이었습니다.

<u>필수 구성 요소:</u>:

Adobe Commerce B2B 모듈을 설치하고 활성화합니다.

<u>재현 단계</u>:

1. 회사를 만듭니다.
1. 아래 돌연변이로 GraphQL에 회사 관리자로 로그인합니다.

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. 결과 토큰을 **인증** 요청 헤더에 `Bearer` 토큰으로 추가하고 GraphQL 쿼리 아래에서 실행합니다.

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u>예상 결과</u>:

GraphQL 쿼리는 역할을 반환합니다.

<u>실제 결과</u>:

회사의 역할이 null입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
