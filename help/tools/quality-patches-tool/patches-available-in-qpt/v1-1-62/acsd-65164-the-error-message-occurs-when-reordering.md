---
title: 'ACSD-65164: 단일 확인란 사용자 지정 옵션을 선택하여 구성 가능한 제품을 재정렬할 때 오류 메시지가 표시됩니다'
description: ACSD-65164 패치를 적용하여 단일 선택 확인란 사용자 지정 옵션으로 구성 가능한 제품을 재정렬할 때 *선택한 항목 옵션 중 일부를 현재 사용할 수 없음*이라는 오류 메시지가 표시되는 Adobe Commerce 문제를 수정합니다.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164: 단일 확인란 사용자 지정 옵션을 선택하여 구성 가능한 제품을 재정렬할 때 오류 메시지가 표시됩니다

ACSD-65164 패치는 단일 선택 확인란 사용자 지정 옵션으로 구성 가능한 제품을 다시 정렬할 때 *선택한 항목 옵션 중 일부를 현재 사용할 수 없습니다* 오류 메시지가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65164입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

단일 확인란 사용자 지정 옵션을 선택하여 구성 가능한 제품을 다시 정렬하면 시스템에서 오류 메시지를 반환합니다. *선택한 항목 옵션 중 일부를 현재 사용할 수 없습니다*.

### 복제 단계:

1. 관리 패널에서 **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**(으)로 이동합니다.
1. **[!UICONTROL Customizable Options]**&#x200B;에서 *Checkbox* 옵션을 추가하십시오.
   * 확인란 옵션을 *필수*(으)로 설정하십시오.
   * 두 개의 옵션 값을 추가합니다.
1. Storefront로 이동하여 등록된 고객으로 로그인합니다.
1. 확인란 옵션 하나를 선택한 상태로 제품을 장바구니에 추가합니다.
1. **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**(으)로 이동합니다.
1. 동일한 제품을 추가하려면 **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]**(으)로 이동합니다.

**예상 결과:**

제품을 장바구니에 추가해야 합니다.

**실제 결과:**

오류 메시지가 표시됩니다.

*SKU가 &quot;24-MB01&quot;인 제품을 장바구니에 추가할 수 없습니다. 선택한 항목 옵션 중 일부를 현재 사용할 수 없습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
