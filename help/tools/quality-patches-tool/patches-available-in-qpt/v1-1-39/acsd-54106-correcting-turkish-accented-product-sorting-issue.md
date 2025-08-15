---
title: 'ACSD-54106: 제품 범주에서 터키어 악센트 부호 문자 정렬'
description: ACSD-54106 패치를 적용하여 터키어 악센트 부호 문자에 대한 이름별 카테고리 제품 정렬이 잘못된 Adobe Commerce 문제를 해결합니다.
feature: Categories, Products, Search
role: Admin
exl-id: 45c8efbb-85d0-4d25-9d7e-9c41a97e80fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-54106: 제품 범주에서 터키어 악센트 부호 문자 정렬

ACSD-54106 패치를 사용하면 터키어 악센트 부호 문자에 대한 이름별 범주 제품 정렬이 올바르지 않은 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39가 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-54106입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

터키어 악센트 부호가 있는 문자에 대해 카테고리 내의 제품 정렬이 잘못되었습니다.

<u>재현 단계</u>:

1. 관리 패널에 로그인합니다.
1. 다음과 같이 이름이 지정된 간단한 제품을 만들고 모든 카테고리에 지정합니다.

* 이름 A
* 이름 Ç
* 이름 D
* 이름
* 이름 M
* 이름 외
* 이름 Ü
* 이름 Y
* 이름 Z

1. 상점으로 이동하여 제품이 포함된 범주에 액세스합니다.
1. 정렬 순서를 *[!UICONTROL By Name]*(으)로 수정합니다.

<u>예상 결과</u>:

제품이 다음 순서로 올바르게 정렬됩니다.

* 이름 A
* 이름 Ç
* 이름 D
* 이름
* 이름 M
* 이름 외
* 이름 Ü
* 이름 Y
* 이름 Z

<u>실제 결과</u>:

제품이 다음 순서로 잘못 정렬되었습니다.

* 이름 A
* 이름 D
* 이름 M
* 이름 Y
* 이름 Z
* 이름 Ç
* 이름 외
* 이름 Ü
* 이름

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
