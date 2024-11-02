---
title: 'MDVA-37897: 최근에 본 항목에서 제품을 추가할 때 잘못된 리디렉션'
description: MDVA-37897 패치는 사용자가 최근에 본 위젯의 옵션으로 제품을 추가하려고 할 때 잘못된 리디렉션 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37897입니다. 이 문제는 Adobe Systems Commerce 버전 2.4.4에서 수정될 예정입니다.
feature: Products
role: Admin
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897: 최근에 본 항목에서 제품을 추가할 때 잘못된 리디렉션

MDVA-37897 패치는 사용자가 최근에 본 위젯의 옵션으로 제품을 추가하려고 할 때 잘못된 리디렉션 문제를 해결합니다. 이 패치는 QPT(Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1이 설치된 경우 [사용할 수 있습니다. 패치 ID는 MDVA-37897입니다. 이 문제는 Adobe Commerce 버전 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Systems Commerce 버전과 호환 가능:**

* Adobe Systems Commerce(모든 배포 방법) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 Quality Patches Tool 릴리스가 있는 다른 버전에 적용될 수 있습니다. 패치가 Adobe Systems Commerce 버전과 호환되는지 확인하려면 패키지를 최신 버전으로 업데이트 `magento/quality-patches` 하고 : Search 패치 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 대한 호환성[[!DNL Quality Patches Tool]을 확인하십시오. 패치 ID를 검색 키워드 역할을 하여 패치를 찾습니다.

## 출판하다

사용자가 최근에 본 항목 섹션에서 필수 옵션을 선택해야 하는 제품을 추가하려고 하면 사용자가 제품 세부 정보 페이지 대신 제품 목록 페이지 페이지로 리디렉션됩니다.

<u>재현</u> 단계 :

1. 사용자 정의 가능한 옵션을 사용하여 간단한 제품을 만듭니다(유형: 라디오 단추).
1. 제품을 표시하도록 최근에 본 위젯을 구성합니다.
1. 최근에 본 위젯에 표시되도록 사용자 정의 가능한 옵션이 있는 제품을 방문하십시오.
1. 최근에 본 위젯의 제품 중 하나에서 **장바구니에 추가**&#x200B;를 클릭합니다.

<u>예상 결과</u>:

옵션을 선택할 수 있는 제품 세부 사항 페이지 페이지로 리디렉션됩니다.

<u>실제 결과</u>:

제품 목록 페이지 페이지로 리디렉션됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용하십시오.

* Adobe Commerce 온-프레미스: 개발자 설명서에서 [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [안내서 내의 Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 사용하여 Adobe Systems Commerce 문제에 사용할 수 있는 패치가 [!DNL Quality Patches Tool] 있는지 확인하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 자세한 내용은 QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)에서 사용할 수 있는 패치 섹션을 참조하세요[.
