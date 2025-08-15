---
title: 'ACSD-64684: 쉼표가 1,000(1,000)로 인해 999를 초과하는 값의 기프트 카드를 저장할 때 유효성 검사 오류 발생'
description: ACSD-64684 패치를 적용하여 "1,000"의 쉼표로 인해 값이 999가 넘는 기프트 카드를 저장할 때 유효성 검사 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management
role: Admin, Developer
exl-id: 327c5d28-b52c-4da9-a905-8a3deb755241
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64684: 쉼표가 1,000(1,000)로 인해 999를 초과하는 값의 기프트 카드를 저장할 때 유효성 검사 오류 발생

ACSD-64684 패치는 쉼표가 &quot;1,000&quot;(으)로 인해 999가 넘는 기프트 카드를 저장할 때 유효성 검사 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64684입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

&#39;1,000&#39;(1,000)과 같은 숫자의 쉼표(천 단위 구분 기호)로 인해 값이 999보다 큰 기프트 카드를 편집하고 저장할 때 유효성 검사 오류가 발생합니다.

<u>재현 단계</u>:

1. 기프트 카드 제품을 만듭니다.
   1. 1,000을 [!UICONTROL Amount]&#x200B;(으)로 입력합니다.
   1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

* 1,000원이 포함된 새 기프트 카드가 적립되었습니다.

<u>실제 결과</u>:

* 기프트 카드 금액이 999보다 큰 경우 유효성 검사 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
