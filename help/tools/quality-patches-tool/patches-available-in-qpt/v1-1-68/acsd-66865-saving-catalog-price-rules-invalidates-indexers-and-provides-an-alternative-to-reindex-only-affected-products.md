---
title: 'ACSD-66865: [!UICONTROL Catalog Price Rule]을(를) 저장하면 인덱서가 무효화되고 영향을 받는 제품만 다시 인덱싱하는 대체 방법이 제공됩니다.'
description: 'ACSD-66865 패치를 적용하여 Adobe Commerce 문제 해결 위치:  [!UICONTROL Catalog Price Rules]을(를) 저장하면 인덱서가 무효화되고 영향을 받는 제품만 다시 인덱싱하는 대체 방법이 제공됩니다.'
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865: **[!UICONTROL Catalog Price Rule]**&#x200B;을(를) 저장하면 인덱서가 무효화되고 영향을 받는 제품만 다시 인덱싱하는 대체 방법이 제공됩니다.

ACSD-66865 패치는 **[!UICONTROL Catalog Price Rule]**&#x200B;을(를) 저장하면 인덱서가 무효화되고 영향을 받는 제품만 다시 인덱싱하는 대안을 제공하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66865입니다. 이 문제는 Adobe Commerce 2.4.8에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Catalog Price Rule]**&#x200B;을(를) 저장하면 모든 인덱서가 무효화되므로 영향을 받는 제품만 다시 인덱싱하는 대신 전체 다시 인덱싱이 트리거됩니다.

<u>재현 단계</u>:

1. 크론이 실행되고 있지 않은지, 모든 인덱서가 일정에 따라 업데이트되도록 설정되어 있는지 확인하십시오(저장 시 업데이트할 수 있는 `customer_grid` 제외).
2. `php bin/magento indexer:reindex` 명령을 사용하여 전체 수동 색인 재지정을 실행합니다.
3. 백로그에 *[!UICONTROL Ready]* 0 *항목이 있는 모든 인덱스가* 상태를 표시하는지 확인하십시오.
4. 관리 사이드바에서 **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**(으)로 이동합니다. 단일 제품에 대한 활성 카탈로그 가격 규칙을 만듭니다(예: *SKU* 조건 사용).
5. `php bin/magento indexer:status` 명령을 실행하여 인덱서 상태를 확인합니다.
6. 한 제품만 영향을 받는 경우에도 여러 인덱스가 **[!UICONTROL Reindex Required]**(으)로 표시되는지 확인하십시오.

<u>예상 결과</u>:

영향을 받는 제품 데이터만 식별되며 모든 인덱서에서 전체 리인덱스 대신 부분 리인덱스가 트리거됩니다.

<u>실제 결과</u>:

단일 제품만 **[!UICONTROL Catalog Price Rule]**&#x200B;의 영향을 받는 경우에도 모든 인덱서에 대해 전체 색인 재지정이 트리거됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
