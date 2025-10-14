---
title: 'ACSD-60344: 자동 승인으로 [!UICONTROL Purchase Order]을(를) 사용할 때 주문 확인 전자 메일이 중복됨'
description: ACSD-60344 패치를 적용하여 자동 승인으로 [!UICONTROL Purchase Order]을(를) 사용할 때 중복 주문 확인 전자 메일이 전송되는 Adobe Commerce 문제를 해결합니다.
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: 자동 승인으로 *[!UICONTROL Purchase Order]*&#x200B;을(를) 사용할 때 주문 확인 전자 메일이 중복됨

ACSD-60344 패치는 자동 승인으로 *[!UICONTROL Purchase Order]*&#x200B;을(를) 사용할 때 중복 주문 확인 전자 메일이 전송되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-60344입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

자동 승인으로 *[!UICONTROL Purchase Order]*&#x200B;을(를) 사용하는 경우 중복 주문 확인 전자 메일이 전송됩니다.

<u>필수 구성 요소</u>

B2B 모듈 및 *[!UICONTROL Purchase Order]*&#x200B;을(를) 사용하도록 설정합니다.

<u>재현 단계</u>:

1. 회사 계정을 만들고 *[!UICONTROL Purchase Order]*&#x200B;을(를) 사용하도록 설정합니다.
1. 일반 사용자 계정을 만든 후 회사 사용자로 회사 계정에 추가합니다.
1. 이 계정을 사용하여 주문합니다.
1. cron을 실행하고 이메일을 확인합니다.

<u>예상 결과</u>:

주문당 하나의 주문 확인 이메일만 수신됩니다.

<u>실제 결과</u>:

두 개의 주문 확인 이메일이 수신됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
