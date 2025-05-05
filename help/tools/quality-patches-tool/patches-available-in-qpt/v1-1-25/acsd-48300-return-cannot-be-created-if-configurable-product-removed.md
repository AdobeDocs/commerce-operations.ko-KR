---
title: 'ACSD-48300: 구성 가능한 제품을 제거하면 반환을 만들 수 없습니다.'
description: ACSD-48300 패치를 적용하여 구성 가능한 제품이 제거된 경우 반환을 만들 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
exl-id: 50139364-e2ea-47a8-9bca-09876dd0e70d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-48300: 구성 가능한 제품을 제거하면 반환을 만들 수 없습니다.

ACSD-48300 패치는 구성 가능한 제품이 제거될 경우 반환을 만들 수 없는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-48300입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품을 제거하면 반품을 생성할 수 없습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**&#x200B;의 상점 첫 화면에서 RMA를 활성화합니다.
1. 구성 가능한 제품을 만듭니다.
1. 상점 첫 화면에서 계정을 만듭니다 (및/또는 로그인).
1. 구성 가능한 제품을 장바구니에 첫 번째 항목으로 추가합니다.
1. 이후에 간단한 제품을 추가합니다.
1. 주문하십시오.
1. 주문을 배송합니다.
1. 이제 구성 가능한 제품만 삭제합니다(하위 제품은 삭제하지 마십시오).
1. 상점 앞에서 **[!UICONTROL My Orders]**(으)로 이동하여 주문을 확인합니다.
1. **[!UICONTROL Return]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

관리자는 구성 가능한 제품이 삭제되더라도 항목을 반환할 수 있습니다.

<u>실제 결과</u>:

항목을 반환할 때 오류가 발생합니다.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
