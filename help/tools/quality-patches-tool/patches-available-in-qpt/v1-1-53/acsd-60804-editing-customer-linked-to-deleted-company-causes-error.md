---
title: 'ACSD-60804: 삭제된 회사와 연결된 고객을 편집하면 오류가 발생합니다'
description: ACSD-60804 패치를 적용하여 삭제된 회사와 연결된 고객을 편집하면 null*에서 멤버 함수 getSuperUserId()를 호출하는 *오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-60804: 삭제된 회사와 연결된 고객을 편집하면 오류가 발생합니다

ACSD-60804 패치는 삭제된 회사와 연결된 고객을 편집하면 null *에 멤버 함수 getSuperUserId()를 호출하는*&#x200B;오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-60804입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

삭제된 회사와 연결된 고객을 편집하면 null *에 멤버 함수 getSuperUserId()를 호출하는 동안*&#x200B;오류가 발생합니다.

<u>필수 구성 요소:</u>:

Adobe Commerce B2B 모듈을 설치하고 활성화합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**(으)로 이동합니다.
1. **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**(으)로 이동합니다.
1. 인스턴스의 `mysql`에 로그인합니다.
1. `entity_id` = *1*&#x200B;인 회사를 삭제합니다.
1. **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**(으)로 이동합니다.
1. 회사를 만들 때 자동으로 만든 고객을 편집합니다.

<u>예상 결과</u>:

고객이 예외 오류 없이 편집됩니다.

<u>실제 결과</u>:

오류가 발생했습니다. 고객과 연결된 회사가 없는 경우 *null에 멤버 함수 getSuperUserId()를 호출합니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
