---
title: 'ACSD-64546: UPS 레이블 생성 중 UI 및 배열에서 문자열 전환 예외에 일반적인 오류 메시지'
description: ACSD-64546 패치를 적용하여 UI에 일반 오류 메시지가 나타나고 UPS 레이블 생성 중 문자열에 대한 배열 전환 예외가 기록되는 Adobe Commerce 문제를 해결합니다. 이 패치를 사용하면 UI 및 로그에 올바른 오류가 표시됩니다.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546: UPS 레이블을 만드는 동안 UI 및 *문자열 변환에 대한 배열* 예외에 일반 오류 메시지가 표시됨

ACSD-64546 패치는 UI에 일반 오류 메시지가 나타나고 UPS 레이블을 만드는 동안 *문자열 변환에 대한 배열* 예외가 기록되는 문제를 해결하여 UI 및 로그에 올바른 오류가 표시되도록 합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64546입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

UI에 일반 오류 메시지가 표시되고 UPS 레이블을 만드는 동안 *문자열 변환에 대한 배열* 예외가 발생합니다.

<u>재현 단계</u>:

1. 유효한 주소로 고객 계정을 만드십시오.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]**(으)로 이동하여 올바른 주소를 추가하십시오.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]**(으)로 이동하여 올바른 주소를 추가하십시오.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]**(으)로 이동하여 UPS를 구성합니다.
1. [!UICONTROL UPS]을(를) 사용하여 주문합니다.
1. 데이터베이스의 `core_config_data`에서 UPS 사용자 ID 및 암호를 제거하십시오.
1. 구성 캐시를 정리합니다.
1. **[!UICONTROL Admin]**&#x200B;에서 만들어진 순서를 엽니다.
1. 새 선적을 생성합니다.
   1. **[!UICONTROL Create Shipping Label]** 확인란을 선택합니다.
   1. **[!UICONTROL Submit shipment]**&#x200B;을(를) 클릭합니다.
   1. 제품을 패키지에 추가합니다. 패키지 크기(길이, 너비 및 높이)를 지정합니다.
   1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

실제 오류 메시지가 UI 및 로그에 표시됩니다.

<u>실제 결과</u>:

* UI에 다음 오류가 나타납니다.
  *배송 레이블을 만드는 동안 오류가 발생했습니다.*
* *문자열 변환에 대한 배열* 예외로 인해 실제 오류 메시지가 로그에 표시되거나 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.
* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.
* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
