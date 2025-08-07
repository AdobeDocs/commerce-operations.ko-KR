---
title: 'ACSD-66233: 관리자가 응답하지 않는 제품 목록 팝업으로 인해 제품을 추가할 수 없음'
description: Visual Merchandiser의 [!UICONTROL Add Product] 팝업이 무기한 로드되기 때문에 관리자가 범주에 제품을 추가할 수 없는 Adobe Commerce 문제를 해결하려면 ACSD-66233 패치를 적용하십시오.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
source-git-commit: 165b62a875747a846b15f8f86b036e67704ebc8e
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-66233: 응답하지 않는 제품 목록 팝업으로 인해 관리자가 제품을 추가할 수 없음

ACSD-66233 패치는 Visual Merchandiser의 [!UICONTROL Add Product] 팝업이 무기한 로드되기 때문에 관리자가 범주에 제품을 추가할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66233입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

시각적 머천다이저의 [!UICONTROL Add Product] 팝업이 무기한 로드되어 관리자가 카테고리에 제품을 추가할 수 없는 문제.

<u>재현 단계</u>:

1. 인벤토리 모듈을 설치하고 활성화합니다.
1. 많은 수의 인벤토리 소스를 만듭니다(예: 700개).
1. 여러 재고 재고(예: 12)를 생성하고 재고 출처를 지정합니다.
1. 일부 제품을 만들고 재고 출처에 할당합니다.
1. 카테고리를 만듭니다.
1. [!UICONTROL Products in Category] 섹션을 확장합니다.
1. [!UICONTROL Add Product] 단추를 클릭합니다.
1. 제품 목록과 함께 팝업을 관찰합니다.

<u>예상 결과</u>:

제품 목록은 합리적인 시간 내에 팝업에 로드됩니다.

<u>실제 결과</u>:

팝업이 무기한 로드되고 제품 목록을 표시하지 못합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
