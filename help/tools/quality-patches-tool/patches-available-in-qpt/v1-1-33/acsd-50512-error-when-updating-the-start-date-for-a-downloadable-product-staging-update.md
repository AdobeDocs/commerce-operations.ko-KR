---
title: 'ACSD-50512: 다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 오류 발생'
description: ACSD-51892 패치를 적용하여 *다운로드 가능한 링크가 제품과 관련이 없는 경우 발생하는 Adobe Commerce 성능 문제를 해결합니다.링크를 확인하고 다시 시도하십시오*. 이 오류는 다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 발생합니다.
feature: Products, Staging
role: Admin
exl-id: 9c3b4d45-c500-46a7-8679-a8aa9e0a66d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512: 다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 오류 발생

ACSD-50512 패치를 사용하면 오류 *다운로드 가능한 링크가 제품과 관련이 없는 문제가 해결됩니다. 다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 링크를 확인하고 다시 시도하십시오*. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51502입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

오류 *다운로드 가능한 링크가 제품과 관련이 없습니다. 다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 링크를 확인하고 다시 시도하십시오*.

<u>재현 단계</u>:

1. *다운로드 가능한 링크* 및 *샘플 링크*&#x200B;를 사용하여 다운로드 가능한 제품을 만드십시오.
1. 동일한 제품에 대해 예약된 업데이트를 만들고 제품을 저장합니다.
1. 사전 구성된 예약 업데이트(2단계 이후)를 편집하고 시작 날짜를 변경합니다.
1. 예약된 업데이트를 저장합니다.

<u>예상 결과</u>:

예약된 업데이트에 대한 변경 사항이 정상적으로 저장되었습니다.

<u>실제 결과</u>:

오류 발생: *다운로드 가능한 링크가 제품과 관련이 없습니다. 링크를 확인하고*&#x200B;을(를) 다시 시도하십시오.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
