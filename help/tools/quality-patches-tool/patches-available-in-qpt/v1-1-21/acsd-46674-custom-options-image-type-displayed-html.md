---
title: 'ACSD-46674: 고객 이메일에서 HTML으로 표시되는 이미지 유형의 맞춤형 옵션'
description: ACSD-46674 패치를 적용하여 이미지 유형의 사용자 지정 옵션이 고객 이메일에서 HTML으로 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Communications, Personalization
role: Developer
exl-id: 123ca7b5-02da-4573-897f-ff8adb184389
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-46674: 고객 이메일에서 HTML으로 표시되는 이미지 유형의 맞춤형 옵션

ACSD-46674 패치는 고객 이메일에서 이미지 유형의 사용자 지정 옵션이 HTML으로 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-46674입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이미지 유형의 사용자 지정 옵션은 고객 이메일에서 HTML으로 표시됩니다.

<u>재현 단계</u>:

1. 사용자 지정 옵션으로 제품을 만듭니다.
   * 옵션 유형: *파일*
   * 호환 파일 확장명: *png, jpg, gif*
   * 필수: *예*
1. 이미지가 사용자 정의 옵션으로 업로드된 상태로 이 제품을 주문합니다.
1. 2단계에서 생성된 주문에 대한 송장을 생성합니다.
1. 대변 메모를 생성합니다.
1. 모든 확인 이메일을 확인합니다.

<u>예상 결과</u>:

확인 이메일에 업로드된 이미지가 표시됩니다.

<u>실제 결과</u>:

확인 이메일에는 제품 사용자 지정 옵션 이미지 대신 일반 HTML 코드가 포함되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tools] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


[!DNL QPT]에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
