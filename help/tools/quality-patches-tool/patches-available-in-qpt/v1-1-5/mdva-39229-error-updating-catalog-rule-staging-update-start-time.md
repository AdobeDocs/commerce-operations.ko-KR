---
title: 'MDVA-39229: 카탈로그 규칙 준비 업데이트 시작 시간을 업데이트한 후 오류 발생'
description: MDVA-39229 패치는 카탈로그 규칙 스테이징 업데이트의 시작 시간을 업데이트한 후 사용자에게 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39229입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: Catalog Management, Staging
role: Admin
exl-id: 633123bc-634c-4943-a2f1-9a48999774f4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-39229: 카탈로그 규칙 준비 업데이트 시작 시간을 업데이트한 후 오류 발생

MDVA-39229 패치는 카탈로그 규칙 스테이징 업데이트의 시작 시간을 업데이트한 후 사용자에게 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39229입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.3.4-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카탈로그 규칙 스테이징 업데이트의 시작 시간을 업데이트한 후 오류가 발생합니다.

<u>재현 단계</u>:

1. 카탈로그 가격 규칙을 만듭니다.
1. 모든 스테이징 업데이트를 만들고 실행합니다.
1. 쿼리를 실행하고 스테이징 플래그가 만들어졌는지 확인하십시오.


   `select * from flag;`


1. 5분 후에 시작할 새 스테이징 업데이트를 만듭니다.
1. **콘텐츠** > **스테이징** > **대시보드** > **새 업데이트**&#x200B;를 열고 시작 시간을 1분 지연하세요.
1. 6분만 기다려주세요
1. 크론 실행

<u>예상 결과</u>:

업데이트 시작 시간이 변경되고 업데이트가 적용됩니다. `staging_update` 테이블에서 이전 업데이트가 삭제되었습니다.

<u>실제 결과</u>:

사용자에게 다음 오류가 표시됩니다.

*report.ERROR: Cron 작업 staging_synchronize_entities_period에 오류가 있습니다. 활성 업데이트를 삭제할 수 없습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko) 섹션을 참조하십시오.
