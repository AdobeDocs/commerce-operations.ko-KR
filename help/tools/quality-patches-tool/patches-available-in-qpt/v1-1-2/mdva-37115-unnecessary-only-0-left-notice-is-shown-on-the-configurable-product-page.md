---
title: 'MDVA-37115: 제품 페이지에 "0개만 남음" 알림이 표시됨'
description: MDVA-37115 패치는 구성 가능한 제품 페이지에 불필요하게 *0개만 남아* 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37115입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
feature: Configuration, Products, Orders
role: Admin
exl-id: ba94b2fd-6a7d-4194-afd8-798854431b57
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-37115: 제품 페이지에 &quot;0개만 남음&quot; 알림이 표시됨

MDVA-37115 패치는 구성 가능한 제품 페이지에 불필요한 *왼쪽 0개만* 알림이 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37115입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 유형) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 유형) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품 페이지에 불필요한 *0개만 남음* 알림이 표시됩니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 몇 가지 옵션을 사용하여 구성 가능한 제품을 만듭니다.
1. 프론트엔드로 가세요
1. 구성 가능한 제품 페이지를 열고 옵션을 선택합니다.

<u>예상 결과</u>:

제품 페이지에 *남은 알림 0개*&#x200B;만 표시됩니다.

<u>실제 결과</u>:

제품 페이지에 *0개의 알림만 표시됩니다*.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
