---
title: 'ACSD-62475: 장바구니에서 기프트 카드 병합 문제를 수정합니다'
description: ACSD-62475 패치를 적용하여 다른 세부 정보가 있는 기프트 카드 제품이 장바구니의 단일 라인 항목으로 잘못 병합되는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475: 장바구니에서 기프트 카드 병합 문제를 수정합니다

ACSD-62475 패치는 다른 세부 정보가 있는 기프트 카드 제품이 장바구니의 단일 라인 항목으로 잘못 병합되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62475입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 추가된 기프트 카드 제품이 고유 발신자 또는 수신자 세부 정보로 잘못 병합되어 데이터가 일치하지 않습니다.

<u>재현 단계</u>:

1. 다음 설정으로 [!UICONTROL Gift Card] 제품을 만드십시오.
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. 상점 첫 화면에서 새 사용자를 만들고 로그인합니다.

1. 기프트 카드 제품을 장바구니에 추가합니다. 자세한 내용은 다음과 같습니다.
   * **[!UICONTROL Sender Name]**: 보낸 사람 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]: 받는 사람 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. 로그아웃

1. 동일한 기프트 카드 제품을 다음 세부 정보와 함께 장바구니에 추가합니다.
   * **[!UICONTROL Sender Name]**: 보낸 사람 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]: 받는 사람 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. 다시 로그인하고 장바구니를 확인합니다.

<u>예상 결과</u>:

두 기프트 카드 모두 각 세부 사항이 있는 두 개의 개별 라인 항목으로 표시되어야 합니다.

<u>실제 결과</u>:

기프트 카드는 수량이 2인 하나의 라인 항목으로 병합되며 첫 번째 기프트 카드의 세부 정보를 유지합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
