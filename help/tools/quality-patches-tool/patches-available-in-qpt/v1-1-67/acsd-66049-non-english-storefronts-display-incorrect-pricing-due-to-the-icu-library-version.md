---
title: 'ACSD-66049: 비영어 상점은 ICU 라이브러리 버전으로 인해 잘못된 가격을 표시합니다.'
description: ACSD-66049 패치를 적용하여 영어가 아닌 상점 전면이 이전 PHP 환경에서 ICU 라이브러리 버전이 일치하지 않아 잘못된 가격이 표시되는 Adobe Commerce 문제를 해결합니다(버전 63.1 ~ 74.1).
feature: Products
role: Admin, Developer
type: Troubleshooting
exl-id: e667d462-87f6-4db5-bf3f-3213edac2f09
source-git-commit: da11e8bd5c4937ec2a7e548ce487797b83f8fd27
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-66049: 비영어 상점은 ICU 라이브러리 버전으로 인해 잘못된 가격을 표시합니다.

ACSD-66049 패치는 이전 PHP 환경에서 ICU 라이브러리 버전이 일치하지 않아 영어가 아닌 상점 앞에 잘못된 가격이 표시되는 문제를 해결합니다(버전 63.1 ~ 74.1). 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66049입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

영어가 아닌 상점들은 이전 PHP ICU 라이브러리 버전(63.1 ~ 74.1)을 사용할 때 잘못된 가격을 표시합니다.

<u>재현 단계</u>:

1. ICU 버전 확인:
   * SSH를 통해 서버에 연결하고 명령을 실행합니다. `php -a`
   * 프롬프트에서 다음을 입력하십시오. `echo INTL_ICU_VERSION;`
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**&#x200B;로 이동합니다. **[!UICONTROL Configure Locale]** = *[!UICONTROL Hebrew (Israel)]*.
1. 가격 = 100인 제품을 생성합니다.
1. 상점 첫 화면에서 제품 페이지를 봅니다.

<u>예상 결과</u>:

표시된 가격이 0이 아닙니다.

<u>실제 결과</u>:

100으로 잠깐 나타난 후, 가격은 즉시 0으로 업데이트된다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
