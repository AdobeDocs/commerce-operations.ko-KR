---
title: 'ACSD-44851: 열거나 확장할 수 없는 하위 범주가 있는 범주'
description: 이 문서에서는 사용자가 하위 범주가 있는 범주를 열거나 확장할 수 없는 문제에 대한 해결 방법을 제공합니다.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851: 열거나 확장할 수 없는 하위 범주가 있는 범주

ACSD-44851 패치는 사용자가 하위 범주가 있는 범주를 열거나 확장할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-44851입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 하위 범주가 있는 범주를 열거나 확장할 수 없습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자에서 두 개의 루트 범주와 각 범주에 대한 몇 개의 하위 범주가 있는 범주 트리를 만듭니다.
1. 레이아웃이 모바일로 바뀔 때까지 모바일 보기/에뮬레이터를 열거나 창 너비를 줄입니다.
1. 카탈로그의 메인 메뉴를 엽니다.
1. 루트 범주를 확장해 보십시오.
1. 범주를 열어 보십시오.

<u>예상 결과</u>:

메뉴에 액세스할 수 있습니다.

<u>실제 결과</u>:

모바일 메뉴의 두 번째 수준이 열리지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: 품질 패치 도구 안내서의 [품질 패치 도구 > 사용량](/help/tools/quality-patches-tool/usage.md).

* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
