---
title: 'ACSD-58108: 조인 테이블 이름이 누락되어 order grid 사용자 지정 모듈 확장에서 SQL 오류가 발생합니다'
description: ACSD-58108 패치를 적용하여 주문 그리드 사용자 정의 모듈 확장에서 누락된 조인 테이블 이름이 특정 열을 필터링할 때 SQL 오류를 발생하는 Adobe Commerce 문제를 수정합니다.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 26009fee51fb81e2517ad09319bac1190d127564
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-58108: 조인 테이블 이름이 누락되어 order grid 사용자 지정 모듈 확장에서 SQL 오류가 발생합니다

ACSD-58108 패치는 주문 그리드 사용자 정의 모듈 확장에서 누락된 조인 테이블 이름이 특정 열을 필터링할 때 SQL 오류를 발생시키는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58108입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

원래 가져오기 테이블에 조인 테이블 이름이 없으면 사용자 지정 모듈 확장을 사용할 때 순서 그리드에 SQL 오류가 발생합니다. 이 문제는 `addFilterToMap` 테이블을 연결한 후 특정 열에 대해 **[!UICONTROL sales_order_item]** 함수가 작동하지 않아 필터링하는 동안 오류가 발생하므로 발생합니다.

<u>재현 단계</u>:

&#x200B;01. 2.4-develop 인스턴스를 설치합니다.
&#x200B;02. 새 주문을 만듭니다.
&#x200B;03. SQL 확장을 사용하여 사용자 지정 모듈을 설치합니다.
&#x200B;04. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동합니다.
&#x200B;05. **[!UICONTROL Purchase Date]** 필터를 적용하고 결과를 기다립니다.
&#x200B;06. **[!UICONTROL Product SKU]** 필터를 적용합니다.

<u>예상 결과</u>:

주문 그리드에서 주문 필터링은 오류 없이 작동합니다.

<u>실제 결과</u>:

주문 그리드에서 필터를 적용할 때 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
