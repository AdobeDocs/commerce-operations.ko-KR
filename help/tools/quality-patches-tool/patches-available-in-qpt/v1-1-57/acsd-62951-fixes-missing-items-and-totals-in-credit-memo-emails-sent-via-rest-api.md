---
title: 'ACSD-62951: REST API를 통해 보낸 [!UICONTROL Credit Memo] 전자 메일의 누락된 항목 및 합계를 수정합니다'
description: ACSD-62951 패치를 적용하여 주문 항목 및 합계를 포함하지 않고 [!UICONTROL Credit Memo] 전자 메일이 전송되는 Adobe Commerce 문제를 해결합니다.
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951: REST API를 통해 보낸 *[!UICONTROL Credit Memo]* 전자 메일의 누락된 항목 및 합계를 수정합니다

ACSD-62951 패치는 주문 항목 및 합계를 포함하지 않고 [!UICONTROL Credit Memo] 전자 메일이 전송되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62951입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.5-p10

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API *[!UICONTROL Credit Memo]*&#x200B;을(를) 통해 대변 메모를 만들 때 전송된 `POST V1/order/:orderId/refund` 전자 메일에는 주문 항목 및 합계가 포함되어 있지 않습니다.

<u>재현 단계</u>:

1. 모든 제품으로 주문을 생성합니다.
1. 주문을 출하하고 송장을 발행합니다. 송장 이메일이 전송되고 제품 세부 정보가 포함되어 있는지 확인합니다.
1. API 클라이언트를 사용하여 관리 토큰을 생성합니다.
1. 토큰을 사용하여 REST API를 통해 대변 메모를 만듭니다.
   1. 끝점: `POST V1/order/:orderId/refund`
   1. 요청 페이로드:

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>예상 결과</u>:

*[!UICONTROL Credit Memo]* 이메일에는 환불 항목 및 합계가 포함되어야 합니다.

<u>실제 결과</u>:

*[!UICONTROL Credit Memo]* 전자 메일에 항목이나 합계가 포함되어 있지 않아 정보가 불완전합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
