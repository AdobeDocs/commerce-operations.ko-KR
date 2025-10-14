---
title: 'ACSD-61366: ''bin/magento setup:static-content:deploy —jobs 4'' 명령에 오류가 발생하며 여러 작업 오류가 발생했습니다.'
description: DB 연결에 대한 포트를 지정했음에도 불구하고 'bin/magento setup:static-content:deploy —jobs 4' 명령에 *호스트 매개 변수* 오류로 여러 작업 오류가 발생하는 Adobe Commerce 문제를 해결하려면 ACSD-61366 패치를 적용합니다.
feature: SCD
role: Admin, Developer
exl-id: d71a4833-a236-429b-a4e5-7d7d51c2caeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366: `bin/magento setup:static-content:deploy --jobs 4` 명령에 오류가 발생하여 여러 작업 오류가 발생했습니다.

ACSD-61366 패치는 DB 연결에 대한 포트를 지정했음에도 불구하고 `bin/magento setup:static-content:deploy --jobs 4`Port를 호스트 매개 변수&#x200B;*오류 내에서 구성해야 하는* 명령에 여러 작업 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61366입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

DB 연결에 대한 포트를 지정했지만 `bin/magento setup:static-content:deploy --jobs 4`호스트 매개 변수 내에서 포트를 구성해야 함&#x200B;*오류가 발생하여* 명령에 여러 작업 오류가 발생했습니다.

<u>재현 단계</u>:

1. `app/etc/env.php`의 데이터베이스 연결에 포트를 지정하십시오.
1. `bin/magento setup:static-content:deploy --jobs 4` 명령을 실행합니다.

<u>예상 결과</u>:

정적 콘텐츠 배포가 성공적으로 완료되었습니다.

<u>실제 결과</u>:

명령이 실패하고 *호스트 매개 변수 내에 포트를 구성해야 합니다* 오류가 발생했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
