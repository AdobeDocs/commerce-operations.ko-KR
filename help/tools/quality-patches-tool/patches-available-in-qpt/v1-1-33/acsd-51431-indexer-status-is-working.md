---
title: 'ACSD-51431: 변경 로그에 항목이 없어도 인덱서 상태는 *[!UICONTROL Working]*입니다.'
description: 변경 로그에 항목이 없어도 인덱서 상태가 *[!UICONTROL Working]*인 Adobe Commerce 문제를 해결하려면 ACSD-51431 패치를 적용합니다.
feature: Logs, Price Indexer
role: Admin
exl-id: c87c059b-f435-468d-a7fe-e6786fdba1f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431: 변경 로그에 항목이 없어도 인덱서 상태는 *[!UICONTROL Working]*&#x200B;입니다.

ACSD-51431 패치는 변경 로그에 항목이 없어도 인덱서 상태가 *[!UICONTROL Working]*&#x200B;인 성능 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51431입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

변경 로그에 항목이 없어도 인덱서 상태는 *[!UICONTROL Working]*&#x200B;입니다.

<u>재현 단계</u>:

1. **[!UICONTROL indexers]**&#x200B;을(를) [!UICONTROL Update on Schedule]&#x200B;(으)로 설정합니다.
1. cron 작업이 매 분마다 실행되도록 구성합니다.
1. 다른 제품에 대한 변경 사항을 동시에 저장합니다.
1. 몇 분 후에 `bin/magento indexer:status`을(를) 실행합니다.

<u>예상 결과</u>:

변경 내용이 처리되었으며 인덱서가 *[!UICONTROL Ready]* 상태입니다. *[!UICONTROL Schedule]* 상태는 *[!UICONTROL idle (0 in the backlog)]*&#x200B;입니다.

<u>실제 결과</u>:

변경 내용이 처리되었으며 인덱서가 *[!UICONTROL Ready]* 상태입니다. 그러나 *[!UICONTROL Schedule]* 상태는 *[!UICONTROL working (0 in the backlog)]*&#x200B;을(를) 표시합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
