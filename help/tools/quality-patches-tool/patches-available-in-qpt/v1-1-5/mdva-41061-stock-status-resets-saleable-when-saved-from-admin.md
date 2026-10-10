---
title: 'MDVA-41061: 관리자로부터 제품을 저장하면 재고 상태가 판매 가능으로 재설정됩니다.'
description: MDVA-41061 패치는 제품이 관리자로부터 저장될 때 재고 상태가 판매 가능으로 재설정되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41061입니다. 최신 패치 버전은 QPT 1.1.15에서 MDVA-41061-V3 패치 ID와 함께 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%
---
# MDVA-41061: 관리자로부터 제품을 저장하면 재고 상태가 판매 가능으로 재설정됩니다.

MDVA-41061 패치는 제품이 관리자로부터 저장될 때 재고 상태가 판매 가능으로 재설정되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41061입니다. 최신 패치 버전은 QPT 1.1.15에서 MDVA-41061-V3 패치 ID와 함께 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자로부터 제품을 저장하면 재고 상태가 판매 가능으로 재설정됩니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 수량 = 1인 간단한 제품을 만듭니다.
1. 1단계에서 생성된 제품을 사용하여 주문합니다.
1. cron 실행 - `cataloginventory_stock_status` 테이블에서 `inventory.reservations.updateSalabilityStatus` 큐가 실행되고 제품 재고 상태가 0으로 변경되었는지 확인하십시오.
1. 프론트엔드에서 제품을 확인하세요. **재고 부족**(으)로 표시되어야 합니다.
1. 변경 없이 제품을 관리자에 저장합니다.

<u>예상 결과</u>:

* 재고 상태를 업데이트할 수 없습니다.
* 제품은 프런트 엔드에서 **품절**&#x200B;되어야 합니다.

<u>실제 결과</u>:

* 간단한 제품은 프런트 엔드에 **재고 중**(으)로 표시되어 있습니다.
* 장바구니에 추가하려고 할 때 *요청된 수량을 사용할 수 없습니다* 메시지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
