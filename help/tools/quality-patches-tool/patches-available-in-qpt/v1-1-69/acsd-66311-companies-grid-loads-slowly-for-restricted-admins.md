---
title: 'ACSD-66311: 제한된 관리자의 사용자에 대해 회사 그리드가 느리게 로드됨'
description: ACSD-66311 패치를 적용하여 웹 사이트 액세스가 제한된 관리자의 경우 회사 그리드가 느리게 로드되는 Adobe Commerce 문제를 해결합니다.
role: Admin, Developer
feature: B2B
type: Troubleshooting
source-git-commit: 841e660136354800dd9758d8c10e86c966be3a1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# ACSD-66311: 제한된 관리자의 사용자에 대해 회사 그리드가 느리게 로드됨

ACSD-66311 패치는 웹 사이트 액세스가 제한된 관리자의 경우 회사 그리드가 느리게 로드되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66311입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

웹 사이트 액세스가 제한된 관리자 사용자의 경우 회사 그리드가 느리게 로드됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL B2B features]**(으)로 Adobe Commerce을 설치합니다.
1. 스토어/뷰를 사용하여 2개의 추가 웹 사이트(기본 웹 사이트 외)를 만듭니다.
   * 기본 웹 사이트(설치 중 생성됨)
   * 웹 사이트 2 → 스토어 2 → StoreView 2
   * 웹 사이트 3 → Store 3 → StoreView 3
1. **[!UICONTROL Admins in Scope]** 사용자 역할 만들기:
   * 범위: 두 개의 스토어: *기본 웹 사이트* + *웹 사이트 3/스토어 3*.
   * 리소스: *대시보드* + *회사*&#x200B;만.
1. **[!UICONTROL Admins in Scope]** 역할이 있는 관리자 사용자를 만드십시오(예: **adminscope**).
1. 특정 분산 고객 및 회사 데이터 생성:
   1. **웹 사이트에 할당된 고객**

      | 웹 사이트 ID | 고객 수 |
      |------------|---------------------|
      | 1 | 600,000 |
      | 2 | 1,500 |
      | 3 | 500 |


   1. 다음 쿼리를 실행하여 배포를 확인합니다.

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **회사에 할당된 고객**

      | 고객 수 | 회사 수 |
      |---------------------|---------------------|
      | 1 | 4,500 |
      | 2 | ~1,000 |
      | ~595k | 1 |

   1. 다음 쿼리를 실행하여 배포를 확인합니다.

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
      
            company_id, COUNT(customer_id) AS customer_count 선택
            출처: company_advanced_customer_entity
            company_id별 그룹
) 하위 쿼리
CUSTOMER_count별 그룹
ORDER BY customer_count;
&quot;

1. 모든 데이터를 다시 인덱싱하여 **customer_grid_flat**&#x200B;에 항목을 생성합니다.
1. **adminscope**(으)로 로그인합니다.
1. **[!UICONTROL Customers]** > **[!UICONTROL Companies]**(으)로 이동합니다.

<u>예상 결과</u>:

페이지가 1초 이내에 로드됩니다.

<u>실제 결과</u>:

페이지를 로드하는 데 14분 이상 걸립니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
