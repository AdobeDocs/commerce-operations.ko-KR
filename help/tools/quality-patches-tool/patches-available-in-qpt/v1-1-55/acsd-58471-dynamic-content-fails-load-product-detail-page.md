---
title: 'ACSD-58471: 연결된 카탈로그 가격 규칙이 예약된 경우 다이내믹 콘텐츠가 제품 세부 사항 페이지에 로드되지 않음'
description: ACSD-58471 패치를 적용하여 관련 카탈로그 가격 규칙이 예정되었을 때 제품 세부 사항 페이지에서 다이내믹 콘텐츠를 로드하지 못하는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471: 연결된 카탈로그 가격 규칙이 예약된 경우 다이내믹 콘텐츠가 제품 세부 사항 페이지에 로드되지 않음

ACSD-58471 패치는 연결된 카탈로그 가격 규칙이 예약되었을 때 제품 세부 사항 페이지에서 동적 콘텐츠를 로드하지 못하는 문제를 해결합니다. 이제 시스템에서 예약된 카탈로그 가격 규칙과 연관된 동적 콘텐츠를 제품 세부 정보 페이지에 올바르게 표시합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-58471입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카탈로그 가격 규칙이 예약된 경우 제품 세부 사항 페이지에 다이내믹 콘텐츠가 로드되지 않습니다.

<u>재현 단계</u>:

1. Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**&#x200B;에서 동적 블록을 만듭니다.
1. [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**&#x200B;에서 정적 블록을 만듭니다. 위젯을 사용하여 컨텐츠를 추가합니다.
1. 제품을 만들고 설명에 CMS 블록을 추가합니다.
1. 예약된 업데이트로 카탈로그 규칙을 만들고 **[!UICONTROL Marketing]** > 프로모션 > **[!UICONTROL Catalog Products Rules]**&#x200B;에서 제품과 생성된 동적 블록을 할당합니다.
1. cron 을 실행하고 제품 세부 사항 페이지에 예약된 시작 시간 이후의 다이내믹 콘텐츠가 표시되는지 확인하십시오.
1. 예약된 업데이트 없이 카탈로그 규칙을 만들고 **[!UICONTROL Marketing]** > 프로모션 > **[!UICONTROL Catalog Products Rules]**&#x200B;에서 제품과 생성된 동적 블록을 할당합니다.
1. cron 을 실행하고 제품 세부 사항 페이지에 예약된 시간 후의 동적 콘텐츠가 표시되는지 확인하십시오.


<u>예상 결과</u>:

동적 콘텐츠는 예약된 시작 시간 후에 로드됩니다.

<u>실제 결과</u>:

다이내믹 콘텐츠가 로드되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
