---
title: 'ACSD-64137: 우편 번호로 픽업 위치 검색이 네덜란드어 현지화에 대해 제대로 작동하지 않음'
description: ACSD-64137 패치를 적용하여 우편번호별 픽업 위치 검색이 네덜란드어 현지화에 대해 제대로 작동하지 않는 문제를 해결합니다.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 86c28b6d-6584-4caf-bd35-13e0c1bdcf1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-64137: 우편 번호로 픽업 위치 검색이 네덜란드어 현지화에 대해 제대로 작동하지 않음

ACSD-64137 패치는 우편번호별 픽업 위치 검색이 네덜란드어 현지화에 대해 제대로 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64137입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

네덜란드 우편 번호 검색 결과가 프론트엔드 체크아웃 페이지에 표시되지 않습니다. 단, 도시별로 작동하며 해당 주소를 검색 없이 표시한다.

<u>재현 단계</u>:

1. 인벤토리 모듈을 사용하여 클린 인스턴스를 설치합니다.
1. 사용자 지정 스톡을 만듭니다.
1. 네덜란드 주소로 두 개의 소스를 만들어 스톡에 할당합니다 (포스트 코드 7311ER 및 7311AE).
1. 간단한 제품을 만들고 인벤토리를 추가합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**(으)로 이동하여 **[!UICONTROL In-Store Delivery]**&#x200B;을(를) 사용하도록 설정합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**(으)로 이동합니다. **[!UICONTROL Provider]**&#x200B;을(를) *오프라인 계산*(으)로 설정합니다.
1. 다음 명령을 실행하여 NL 국가의 지역 이름을 가져옵니다.

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. 제품을 장바구니에 추가하고 배송 단계로 이동합니다.
1. **[!UICONTROL Pick In Store]**&#x200B;을(를) 선택합니다. 그런 다음 **[!UICONTROL Select Other]**&#x200B;을(를) 클릭하여 다른 스토어를 선택합니다.
1. **[!UICONTROL Select Store]** 검색 양식에 *7311* 또는 *7311AE*&#x200B;을(를) 입력하십시오.


**예상 결과**:

* 일치하는 스토어를 채워야 합니다.

**실제 결과**:

* 검색 결과가 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
