---
title: 'ACSD-62872: 예약 업데이트가 잘못 확인됨'
description: ACSD-62872 패치를 적용하여 예약된 업데이트의 유효성이 잘못 검사되는 고유한 속성 유효성 검사로 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
source-git-commit: 4727a94178c642922224cb37ad5c1b2b4f6002cb
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# ACSD-62872: 예약 업데이트가 잘못 확인됨

ACSD-62872 패치는 예약된 업데이트의 유효성이 잘못 검사되는 고유한 속성 유효성 검사 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62872입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>이 패치는 1.1.58 QPT 릴리스에서 버전 2.4.4 - 2.4.6-p8에 대해 더 이상 사용되지 않는 것으로 표시됩니다.

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 속성에 대한 예약된 업데이트의 유효성이 잘못 확인되었습니다.

<u>재현 단계</u>:

1. 범주에 대한 사용자 지정 속성을 만듭니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**(으)로 이동합니다.
1. 새 카테고리를 만듭니다.
1. 같은 범주에서 **[!UICONTROL Scheduled Updates]** 섹션으로 이동합니다.
1. 나중에 언제든지 이 범주에 대한 새 업데이트를 설정하십시오.
1. 예약된 업데이트를 시작하기 전에 범주에 대해 만든 예약 업데이트를 편집해 보십시오.

<u>예상 결과</u>:

예약된 업데이트를 업데이트할 수 있어야 합니다.

<u>실제 결과</u>:

오류가 발생했습니다. *사용자 지정 특성의 값이 고유하지 않습니다. 고유한 값을 설정하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
