---
title: 'ACSD-58828: 클라이언트측 유효성 검사와 함께 빈 필수 필드에 서버측 *주소 필요* 메시지가 표시됨'
description: ACSD-58828 패치를 적용하여 서버측 유효성 검사 메시지 *주소가 필요합니다* 가 클라이언트측 유효성 검사 메시지와 함께 필수 필드가 비어 있는 경우 나타나는 Adobe Commerce 문제를 해결합니다.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828: 클라이언트측 유효성 검사와 함께 빈 필수 필드에 서버측 *주소가 필요합니다* 메시지가 나타납니다

ACSD-58828 패치는 클라이언트측 유효성 검사 메시지와 함께 필수 필드가 비어 있는 경우 서버측 유효성 검사 메시지 *주소 필요*&#x200B;가 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-58828입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

필수 필드가 비어 있는 경우 클라이언트 측 유효성 검사 메시지와 함께 서버 측 유효성 검사 메시지 *주소가 필요합니다*&#x200B;가 나타납니다.

재현 단계:

1. 고객으로 로그인.
1. 장바구니에 제품을 추가합니다.
1. 체크아웃을 진행합니다.
1. 배송 주소는 그대로 두십시오.
1. **[!UICONTROL Flat rate]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL My billing and shipping address are the same]**&#x200B;을(를) 선택 취소합니다.
1. 드롭다운에서 새 주소를 추가합니다.
1. 필수 필드를 비워 두고 **[!UICONTROL Update]**&#x200B;을(를) 선택하십시오.

예상 결과:

오류 메시지에서는 체크아웃에 필요한 정보가 누락되었거나 잘못된 것을 설명합니다.

실제 결과:

오류 *주소가 필요합니다. 을(를) 입력하고 다시 시도하십시오.*&#x200B;이(가) 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
