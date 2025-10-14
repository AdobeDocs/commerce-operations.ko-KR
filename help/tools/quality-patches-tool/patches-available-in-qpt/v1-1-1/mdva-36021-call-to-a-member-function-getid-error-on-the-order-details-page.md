---
title: 'MDVA-36021: 주문 세부 사항을 열 때 사용자에게 오류 메시지가 표시됨'
description: MDVA-36021 패치는 주문 세부 사항을 열려고 할 때 사용자가 멤버 함수 getId()* 오류 메시지에 *호출을 가져오는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36021입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: Orders
role: Admin
exl-id: 737479fe-f363-4974-9c58-7ed9cd113fdb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-36021: 주문 세부 사항을 열 때 사용자에게 오류 메시지가 표시됨

MDVA-36021 패치를 사용하면 주문 세부 정보를 열려고 할 때 사용자가 *멤버 함수 getId()*&#x200B;에 대한 호출을 가져오는 문제가 해결됩니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-36021입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.1, 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 주문 세부 사항을 열려고 하면 관리자의 주문 세부 사항 페이지에 다음 오류 메시지가 표시됩니다. *report.CRITICAL: Error: /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*&#x200B;의 배열에서 멤버 함수 getId()를 호출합니다.

<u>필수 구성 요소</u>:

동 제도는 세율과 세율의 체계를 갖추어야 한다.

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다.
1. **판매** > **주문** > **주문 열기**(으)로 이동합니다.

<u>예상 결과</u>:

주문이 오류 없이 열려 있습니다.

<u>실제 결과</u>:

다음과 유사한 오류 메시지가 표시됩니다. *report.CRITICAL: Error: /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*&#x200B;의 배열에서 멤버 함수 getId()를 호출합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서 &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
