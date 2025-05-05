---
title: 'ACSD-60326: 고객 [!UICONTROL Returns] 상태의 GraphQL 쿼리에서 오류가 발생했습니다.'
description: ACSD-60326 패치를 적용하여 고객 [!UICONTROL Returns] 상태에 대한 GraphQL 쿼리에서 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: 고객 [!UICONTROL Returns] 상태의 GraphQL 쿼리에서 오류가 발생했습니다.

ACSD-60326 패치는 고객 [!UICONTROL Returns] 상태에 대한 GraphQL 쿼리에서 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-60326입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 [!UICONTROL Returns] 상태의 GraphQL 쿼리에서 오류가 발생했습니다.

<u>재현 단계</u>:

1. 샘플 데이터로 새 인스턴스를 초기화합니다.
1. *[!UICONTROL Admin]* 사이드바에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**(으)로 이동한 다음 **[!UICONTROL Enable RMA on Storefront]**&#x200B;을(를) *예*(으)로 설정합니다.
1. **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]**(으)로 이동하여 주소를 입력하십시오.
1. 고객 `roni_cost@example.com`의 암호를 변경합니다.
1. 관리 패널에 로그인하고 고객 `roni_cost@example.com`에게 다음 제품을 주문합니다.
   * *WSH12-32-빨강*
   * *WSH12-32-자주색*
   * *WSH12-32-녹색*
1. 이 주문에 대해 *[!UICONTROL Invoice]* 및 *[!UICONTROL Shipment]*&#x200B;을(를) 만듭니다.
1. **[!UICONTROL Create Returns]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]**(으)로 이동한 다음:
   * *WSH12-32-Red* 및 *WSH12-32-Purple* 선택
   * **[!UICONTROL Add Selected Products to returns]** 클릭:
      * **[!UICONTROL Requested]** = *1* 설정
      * **[!UICONTROL Return Reason]**&#x200B;을(를) *서비스 중단*(으)로 설정
      * **[!UICONTROL Item Condition]**&#x200B;을(를) *열림*(으)로 설정
      * **[!UICONTROL Resolution]**&#x200B;을(를) *환불*(으)로 설정
   * **[!UICONTROL Submit Returns]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Returns]**&#x200B;을(를) 열고 왼쪽의 **[!UICONTROL Return Items]**&#x200B;을(를) 선택합니다.
   * 두 제품에 대해 **[!UICONTROL Authorized]** = *1* 설정
   * *WSH12-32-Purple*&#x200B;에 대해 **[!UICONTROL Status]**&#x200B;을(를) *Authorized*(으)로 설정
   * *WSH12-32-Red*&#x200B;에 대해 **[!UICONTROL Status]**&#x200B;을(를) *거부*(으)로 설정
   * **[!UICONTROL Save]** 클릭
1. 동일한 제품으로 새 주문을 생성합니다.
1. 동일한 제품에 대해 *[!UICONTROL Invoice]*, *[!UICONTROL Shipment]* 및 *[!UICONTROL Returns]*&#x200B;을(를) 만듭니다. 두 가지를 모두 승인하고 [!UICONTROL Returns] 프로세스가 끝날 때까지 진행하십시오.
1. 다음 GraphQL 쿼리를 사용하여 고객 토큰을 생성합니다.

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. 수신된 토큰으로 권한을 부여하고 다음 쿼리를 수행합니다.

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>예상 결과</u>:

쿼리에 오류가 표시되지 않습니다. 두 번째 반환의 상태가 *null*&#x200B;이(가) 아닙니다.

<u>실제 결과</u>:

쿼리가 내부 서버 오류를 반환합니다.

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
