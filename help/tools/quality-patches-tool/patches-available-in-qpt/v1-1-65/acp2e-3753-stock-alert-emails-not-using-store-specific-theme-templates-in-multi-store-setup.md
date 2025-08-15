---
title: 'ACP2E-3753: 다중 스토어 설정에서 스토어 특정 테마 템플릿을 사용하지 않는 스톡 경고 이메일'
description: ACP2E-3753 패치를 적용하여 다중 스토어 설정의 제품 경고 이메일이 스토어 또는 테마 구성에 관계없이 기본 테마를 사용하여 항상 전송되는 Adobe Commerce 문제를 해결합니다.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
source-git-commit: 2089fed83a207f9d0211273652ea320d2590f8d5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACP2E-3753: 다중 스토어 설정에서 스토어 특정 테마 템플릿을 사용하지 않는 스톡 경고 이메일

ACP2E-3753 패치는 다중 스토어 설정의 제품 경고 이메일이 스토어 또는 테마 구성에 관계없이 기본 테마를 사용하여 전송된 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACP2E-3753입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p11

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다중 스토어 설정의 제품 경고 이메일은 스토어 또는 테마 구성에 관계없이 항상 기본 테마를 사용하여 전송됩니다.

<u>재현 단계</u>:

1. 두 개의 웹 사이트, 스토어 및 스토어 조회수를 만듭니다.
1. 두 개의 별도 테마를 만들고 서로 다른 스토어에 할당합니다.
1. 제품 경고 설정은 매분마다 실행되는 기본 범위입니다.
1. 두 테마의 `stock.phtml` 파일에 일부 콘텐츠를 재정의/추가합니다. 파일 위치의 예:

   ```
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. 각 스토어에 대한 사용자를 만들고 제품 스톡 경고를 구독합니다.
1. 이메일을 보내려면 제품 스톡 경고를 트리거합니다.

<u>예상 결과</u>:

이메일에는 테마 수준 변경 사항이 포함되어야 합니다.

<u>실제 결과</u>:

이메일에는 각 웹 사이트/스토어에 설정된 템플릿이 포함되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
