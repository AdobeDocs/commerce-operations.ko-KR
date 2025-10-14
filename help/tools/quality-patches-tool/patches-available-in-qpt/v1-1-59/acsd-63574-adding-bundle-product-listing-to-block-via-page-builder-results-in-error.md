---
title: 'ACSD-63574: [!UICONTROL Bundle Product]을(를) 통해 차단할  [!DNL Page Builder]  목록을 추가하면 오류가 발생합니다.'
description: 'ACSD-63574 패치를 적용하여 ''확인란'' 또는 ''다중 선택'' 옵션이 있는 **[!UICONTROL Bundle Product]**을(를) 통해 블록에 추가하면 오류가 발생하는 Adobe Commerce 문제를 해결합니다. [!DNL Page Builder] '
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574: [!UICONTROL Bundle Product]을(를) 통해 차단할 [!DNL Page Builder] 목록을 추가하면 오류가 발생합니다.

ACSD-63574 패치는 **[!UICONTROL Bundle Product]**&#x200B;을(를) 통해 `Checkbox` 또는 `Multi Select` 옵션이 있는 [!DNL Page Builder]을(를) 블록에 추가하면 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63574입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.4-p10

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Bundle Product]**&#x200B;을(를) 사용하여 [!DNL Page Builder]을(를) 블록에 추가하면 제품 위젯 미리 보기가 중단되고 오류 메시지 *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다*. 이 문제는 특히 번들 제품에 `Checkbox` 또는 `Multi Select` 옵션 유형이 포함되어 있고 `indexer dimension mode`이(가) `website_and_customer_group`(으)로 설정된 경우에 발생합니다. 예외 로그에는 다음 오류가 표시됩니다.

    &quot;
    report.CRITICAL: PDOException: SQLSTATE[42S02]: 기본 테이블 또는 뷰를 찾을 수 없음: 1146 테이블 &#39;db_name.catalog_product_index_price_cg0_ws0&#39;이(가) /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    &quot;
에 없음
<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**(으)로 이동합니다.
1. 왼쪽 패널에서 **[!UICONTROL Catalog]**&#x200B;을(를) 확장하고 아래 옵션에서 **[!UICONTROL Catalog]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Price]** 섹션까지 아래로 스크롤하고 **[!UICONTROL Catalog Price Scope]**&#x200B;을(를) **[!UICONTROL Global]**(으)로 설정합니다.
1. 아래 명령을 사용하여 `Indexer dimension mode`을(를) `website_and_customer_group`(으)로 설정:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. 번들 옵션 유형이 **[!UICONTROL Bundle Product]** 또는 `Checkbox`인 `Multi Select`을(를) 만들고 제품을 범주에 할당합니다.
1. **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**(으)로 이동합니다.
1. 만든 제품이 할당된 범주를 선택하고 **[!UICONTROL Save]**&#x200B;을(를) 시도하십시오.

<u>예상 결과</u>:

제품이 오류 없이 추가되었습니다.

<u>실제 결과</u>:

[!DNL Page Builder] 옵션 유형이 **[!UICONTROL Bundle Product]** 또는 `Checkbox`이고 `Multi Select`이(가) `indexer dimension mode`(으)로 설정된 경우 `website_and_customer_group`을(를) 통해 제품을 추가할 수 없습니다. 오류가 발생합니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다*.


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
