---
title: 'ACSD-45424: 부분 환불 후 생성된 잘못된 예약 보상'
description: ACSD-45424 패치를 사용하면 부분 환불 후 잘못된 예약 보상이 생성되는 문제가 해결됩니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45424입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424: 부분 환불 후 생성된 잘못된 예약 보상

ACSD-45424 패치를 사용하면 부분 환불 후 잘못된 예약 보상이 생성되는 문제가 해결됩니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45424입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

일부 환불 후 잘못된 예약 보상이 생긴다.

<u>재현 단계</u>:

1. 매장 배송 방법을 활성화합니다.
1. 세 개의 인벤토리 소스를 만들고 픽업 위치가 각(source1, source2, source3)에서 활성 상태인지 확인합니다.
1. 새 재고를 생성하고 세 개의 출처를 새 재고에 지정합니다.
   * 이 주식은 메인 웹사이트에 배정되어야 합니다.
1. 간단한 제품인 P3를 만들고 모든 소스를 지정합니다.
1. 단순 제품의 출처에 대해 다음 수량을 추가하고 미납주문을 활성화합니다.
   * 기본 소스 - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. 프론트엔드에서 간단한 제품을 장바구니에 추가하고 배송 양식으로 진행합니다.
1. 배송 위치로 &quot;source1&quot;을 선택합니다.
1. 순서를 완료하고 데이터베이스에서 다음 쿼리를 실행합니다.

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   `inventory_reservation` 테이블에 주문 레코드를 가져옵니다. 수량은 10개이고, 맞다.
1. 백엔드에서 이 주문에 대한 송장을 발행합니다.
1. 이제 하나의 제품에 대해서만 대변 메모를 만듭니다. *상가로 돌아가기* 확인란을 선택하지 마십시오.
1. 8단계에서 동일한 쿼리를 실행합니다.

<u>예상 결과</u>:

대변 메모를 만드는 동안 *주식으로 돌아가기*&#x200B;를 선택하지 않은 경우 `inventory_reservation` 테이블에 대변 메모에 해당하는 레코드가 없습니다.

<u>실제 결과</u>:

대변 메모를 만드는 동안 *상주로 돌아가기*&#x200B;를 선택하지 않았더라도 `creditmemo_created` 이벤트 유형의 `inventory_reservation` 테이블에 레코드가 추가됩니다. 또한 한 개의 수량에 대해서만 대변 메모를 만들었지만 `inventory_reservation` 테이블에 추가된 대변 메모 레코드의 수량은 10입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
