---
title: '제한된 보기가 있는 개인 공유 카탈로그에 대해 ACSD-61895: [!DNL GraphQL] 범주 쿼리가 실패합니다'
description: ACSD-61895 패치를 적용하여 동일한 범주에 대한 제한이 있는 개인 공유 카탈로그를 만들 때 게스트 고객에 대한  [!DNL GraphQL] 응답(모든 허용된 범주가 있는 공용 공유 카탈로그 사용)이 범주를 반환하지 않은 Adobe Commerce 문제를 해결합니다.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
source-git-commit: f929f76dbe79c3764e2c157576b4f6db867673cf
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# ACSD-61895: 보기가 제한된 개인 공유 카탈로그에 대해 [!DNL GraphQL] `categories` 쿼리가 실패합니다

ACSD-61895 패치는 동일한 범주에 대한 제한이 있는 개인 공유 카탈로그를 만들 때 게스트 고객에 대한 [!DNL GraphQL] 응답(모든 허용된 범주가 있는 공용 공유 카탈로그 사용)이 범주를 반환하지 않던 문제를 해결합니다.

수정 후에는 루트 범주에 개인 공유 카탈로그의 범위에서 허용 권한이 없는 경우에도 게스트 사용자에 대해 허용 권한(공용 공유 카탈로그)이 있는 모든 카테고리가 반환됩니다.

이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61895입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 범주에 대해 제한이 있는 개인 공유 카탈로그를 만들 때 게스트 고객에 대한 [!DNL GraphQL] 응답(모든 허용된 범주가 있는 공용 공유 카탈로그 사용)이 범주를 반환하지 않습니다.

<u>재현 단계</u>:

1. B2B 및 샘플 데이터와 함께 Adobe Commerce을 설치합니다.
1. B2B 기능이 활성화되어 있는지 확인합니다.
1. 두 개의 공유 카탈로그(공용 카탈로그 한 개와 개인 카탈로그 한 개)를 만듭니다.

   * 공개 공유 카탈로그:

      * 모든 범주를 공개 카탈로그에 할당합니다.

   * 비공개 공유 카탈로그:

      * `Gear` 범주와 하위 범주만 개인 카탈로그에 할당합니다.
      * 테스트 회사에 비공개 카탈로그를 할당합니다.

1. 회사 사용자 만들기:

   * 비공개 공유 카탈로그에 연결된 테스트 회사와 연결된 사용자를 만듭니다.
   * 로그인할 때 사용자가 `Gear` 범주와 프런트 엔드의 하위 범주에만 액세스할 수 있는지 확인하십시오.

1. API를 통한 쿼리 범주:

   * API 클라이언트를 사용하여 고객 토큰 없이 다음 [!DNL GraphQL] 쿼리를 실행합니다.

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. 응답을 관찰하고 `Gear` 범주와 다른 범주가 반환되는지 확인하십시오.
1. 이제 고객 토큰으로 범주를 쿼리합니다.

   * 테스트 회사 사용자로 로그인
   * 동일한 [!DNL GraphQL] 범주 쿼리를 실행하되 로그인한 사용자에 대한 고객 토큰을 포함하십시오.
   * 응답을 관찰하고 `Gear` 범주와 하위 범주가 반환되는지 확인하십시오.


<u>예상 결과</u>:

게스트 회사 사용자로 쿼리할 때 예상대로 모든 카테고리가 반환되어야 합니다.

<u>실제 결과</u>:

`categories` 쿼리의 응답에 범주가 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).

