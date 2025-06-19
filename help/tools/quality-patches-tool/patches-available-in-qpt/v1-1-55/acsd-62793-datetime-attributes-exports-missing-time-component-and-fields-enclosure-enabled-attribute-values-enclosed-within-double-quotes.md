---
title: 'ACSD-62793: 의 Datetime 속성은 누락된 시간 구성 요소를 내보냅니다. 또한 **[!UICONTROL Fields Enclosure]**이 활성화된 경우 큰따옴표로 묶인 특성 값이'
description: ACSD-62793 패치를 적용하여 내보낸 데이터의 datetime 속성에 시간 구성 요소가 누락되는 Adobe Commerce 문제를 수정합니다. 또한 **[!UICONTROL Fields Enclosure]**이 활성화되어 있으면 *additional_attributes* 열의 특성 값은 큰따옴표로 묶입니다.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
exl-id: 340dcc84-dcb8-40ed-b2ab-2d950d1dd1ca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-62793: 의 Datetime 속성은 누락된 시간 구성 요소를 내보냅니다. 또한 **[!UICONTROL Fields Enclosure]**&#x200B;이(가) 활성화된 경우 특성 값이 큰따옴표로 묶여 있음

ACSD-62793 패치는 내보낸 데이터의 datetime 속성에 시간 구성 요소가 누락되는 문제를 수정합니다. 또한 **[!UICONTROL Fields Enclosure]**&#x200B;을(를) 사용하도록 설정하면 *additional_attributes* 열의 특성 값이 큰따옴표로 묶입니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-62793입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

내보낸 데이터의 날짜/시간 속성에는 시간 구성 요소가 포함되지 않습니다. 또한 **[!UICONTROL Fields Enclosure]**&#x200B;을(를) 사용하도록 설정하면 *additional_attributes* 열의 특성 값이 큰따옴표로 묶입니다.

<u>재현 단계</u>:

1. **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**(으)로 제품 특성을 만듭니다.
1. 특성을 **[!UICONTROL Default]** 특성 집합에 할당합니다.
1. 새 속성에 대한 날짜 및 시간 값이 있는 간단한 제품을 만듭니다.
1. **[!UICONTROL System]** > *데이터 전송* > **[!UICONTROL Export]**&#x200B;에서 제품을 CSV 파일로 내보냅니다.
1. *additional_attributes* 열에서 특성 값을 확인하십시오. 날짜 부분만 있고 시간은 없습니다.
1. 시간을 사용하도록 속성 값을 업데이트합니다(예: &quot;08/10/22, 오후 3:20&quot;).
1. CSV 파일을 가져옵니다.
1. *catalog_product_entity_datetime* 테이블을 확인하십시오.

<u>예상 결과</u>:

날짜 및 시간을 내보내고 제대로 가져옵니다.

<u>실제 결과</u>:

날짜 부분만 내보내고 가져옵니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
