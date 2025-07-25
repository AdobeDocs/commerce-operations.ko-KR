---
title: 'ACSD-66041: CountryID가 누락되어 아일랜드 (IE) 우편 번호를 픽업 위치에서 검색할 수 없음'
description: ACSD-66041 패치를 적용하여 아일랜드 (IE) 포스트코드가 누락된 CountryID 때문에 픽업 위치를 검색할 수 없었던 Adobe Commerce 문제를 해결합니다.
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1f69d00e0ad0caf15643d0c218e1a2c264d3ad4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# ACSD-66041: `CountryID`이(가) 누락되어 아일랜드(IE) 우편 번호를 픽업 위치에서 검색할 수 없음

ACSD-66041 패치는 `CountryID`이(가) 누락되어 아일랜드(IE) 포스트코드를 픽업 위치에서 검색할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66041입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`CountryID`이(가) 누락되어 아일랜드(IE) 우편 번호를 픽업 위치에서 검색할 수 없습니다.

<u>재현 단계</u>:

1. 다음 GraphQL 쿼리를 실행합니다.

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. 다음 변수를 사용하십시오.

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u>예상 결과</u>:

아일랜드 우편 번호는 픽업 장소를 검색하는 데 사용할 수 있습니다.

<u>실제 결과</u>:

* *내부 서버 오류*&#x200B;이(가) 반환됩니다.
* `var/log/exception.log`에 다음 오류가 있습니다.

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
