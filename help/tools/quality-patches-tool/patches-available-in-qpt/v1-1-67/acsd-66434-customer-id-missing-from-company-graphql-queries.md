---
title: 'ACSD-66434: [!UICONTROL Customer ID]이(가) 회사에 없음 [!DNL GraphQL] 쿼리'
description: ACSD-66434 패치를 적용하여 [!UICONTROL Customer ID]이(가) 회사에서 누락되는 Adobe Commerce 문제 [!DNL GraphQL] 를 해결합니다.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
source-git-commit: e60194341bf79ca3ecdc505cf30f226b8f1b6c7f
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# ACSD-66434: [!UICONTROL Customer ID]이(가) 회사 [!DNL GraphQL] 쿼리에 없습니다.

ACSD-66434 패치는 회사 **[!UICONTROL Customer ID]** 쿼리에서 [!DNL GraphQL]이(가) 누락된 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66434입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL GraphQL] 회사 쿼리가 회사 구조의 `null`에 대해 **[!UICONTROL Customer ID]**&#x200B;을(를) 반환합니다.

<u>재현 단계</u>:

1. B2B 및 인벤토리 모듈을 사용하여 Adobe Commerce 2.4-develop을 설치합니다.
1. Commerce 관리에서 B2B 기능을 활성화하고 테스트 회사를 만듭니다.
1. 다음 [!DNL GraphQL] 돌연변이를 사용하여 회사 관리자의 전달자 토큰을 생성합니다.

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. 생성된 토큰을 사용하여 다음 [!DNL GraphQL] 쿼리로 고객의 회사 구조를 검색합니다.

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>예상 결과</u>:

회사 **[!UICONTROL Customer ID]** 쿼리에서 [!DNL GraphQL]을(를) 반환해야 합니다.

<u>실제 결과</u>:

**[!UICONTROL Customer ID]**&#x200B;이(가) 회사 `null` 쿼리에서 [!DNL GraphQL]&#x200B;(으)로 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
