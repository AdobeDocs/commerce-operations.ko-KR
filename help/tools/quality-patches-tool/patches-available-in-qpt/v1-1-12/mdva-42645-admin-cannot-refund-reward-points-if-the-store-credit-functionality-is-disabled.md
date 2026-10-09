---
title: 'MDVA-42645: 관리자가 비활성화된 스토어 크레딧에 대한 보상 포인트를 환불할 수 없음'
description: MDVA-42645 패치는 저장소 신용 기능이 비활성화된 경우 관리자가 보상 포인트를 환불할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42645입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
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
source-wordcount: '510'
ht-degree: 0%
---
# MDVA-42645: 관리자가 비활성화된 스토어 크레딧에 대한 보상 포인트를 환불할 수 없음

MDVA-42645 패치는 저장소 신용 기능이 비활성화된 경우 관리자가 보상 포인트를 환불할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42645입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자는 스토어 신용 기능이 비활성화된 경우 보상 포인트를 환불할 수 없습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 새 고객 계정을 만들고 몇 가지 보상 포인트를 추가합니다.
1. **스토어** > 설정 > **구성** > **고객** > **고객 구성** > **스토어 신용 옵션**&#x200B;으로 이동하여 스토어 신용 기능을 비활성화합니다.
1. 보상 포인트가 지정된 고객으로 로그인합니다.
1. 장바구니에 제품을 추가하고 체크아웃으로 이동합니다.
1. 결제 섹션에서 보상 포인트를 사용한 후 주문합니다.
1. 관리자에서 주문을 열고 주문의 송장을 발행합니다.
1. **대변 메모** 링크를 클릭하여 새 대변 메모를 만듭니다.
1. 맨 아래에 있는 환불 보상 포인트 옵션을 선택하고 **오프라인 환불**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

* 대변 메모가 정상적으로 생성되었습니다.
* 보상 포인트가 성공적으로 환급되었습니다.

<u>실제 결과</u>:

다음 오류 메시지가 나타납니다. *주문 수량보다 더 많은 스토어 크레딧을 사용할 수 없습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
