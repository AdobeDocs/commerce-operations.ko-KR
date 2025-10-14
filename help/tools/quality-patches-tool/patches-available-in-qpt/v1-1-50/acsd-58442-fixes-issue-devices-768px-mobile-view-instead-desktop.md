---
title: 'ACSD-58442: 너비가 768px인 장치가 모바일로 처리되어 메뉴와 헤더가 데스크톱이 아닌 모바일 보기에서 로드되는 문제를 해결했습니다'
description: ACSD-58442 패치를 적용하여 너비가 768px인 장치가 모바일로 처리되어 메뉴와 헤더가 데스크탑 대신 모바일 보기에서 로드되는 Adobe Commerce 문제를 해결합니다.
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-58442: 너비가 768px인 장치가 모바일로 처리되어 메뉴와 헤더가 데스크톱이 아닌 모바일 보기에서 로드되는 문제를 해결했습니다

ACSD-58442 패치는 너비가 768px인 장치가 모바일로 처리되어 메뉴와 헤더가 데스크탑 대신 모바일 보기에서 로드되는 Adobe Commerce 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58442입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이제 시스템에서 너비가 768px인 장치를 데스크탑으로 처리하여 메뉴와 헤더가 올바르게 로드되도록 합니다. 이전에는 너비가 768px인 장치가 모바일로 처리되어 모바일 보기에서 메뉴 및 헤더가 로드되었습니다.

<u>재현 단계</u>:

1. iPad Mini에서 홈 페이지를 로드하거나 브라우저의 검사 도구를 사용하여 브라우저의 크기를 *768px* 너비로 조정하십시오.
1. 메인 메뉴를 엽니다.

<u>예상 결과</u>:

메뉴 및 헤더가 데스크탑 보기로 로드됩니다.

<u>실제 결과</u>:

메뉴 및 헤더가 모바일 보기로 로드됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
