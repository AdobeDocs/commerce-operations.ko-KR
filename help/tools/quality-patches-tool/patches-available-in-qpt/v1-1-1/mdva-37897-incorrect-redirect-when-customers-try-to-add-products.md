---
title: 'MDVA-37897: 최근에 본 제품에서 추가할 때 리디렉션이 잘못됨'
description: MDVA-37897 패치는 사용자가 최근에 본 위젯의 옵션을 사용하여 제품을 추가하려고 할 때 잘못된 리디렉션 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37897입니다. 이 문제는 Adobe Commerce 버전 2.4.4에서 수정됩니다.
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897: 최근에 본 제품에서 추가할 때 리디렉션이 잘못됨

MDVA-37897 패치는 사용자가 최근에 본 위젯의 옵션을 사용하여 제품을 추가하려고 할 때 잘못된 리디렉션 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37897입니다. 이 문제는 Adobe Commerce 버전 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 최근에 본 섹션에서 옵션을 선택해야 하는 제품을 추가하려고 하면 사용자가 제품 세부 사항 페이지 대신 제품 목록 페이지로 리디렉션됩니다.

<u>재현 단계</u>:

1. 사용자 정의 가능한 옵션을 사용하여 간단한 제품을 만듭니다(유형: 라디오 단추).
1. 제품을 표시하도록 최근에 본 위젯을 구성합니다.
1. 최근에 본 위젯에 표시되도록 사용자 정의 가능한 옵션이 있는 제품을 방문하십시오.
1. 최근에 본 위젯의 제품 중 하나에서 **장바구니에 추가**&#x200B;를 클릭합니다.

<u>예상 결과</u>:

옵션을 선택하려면 제품 세부 사항 페이지로 리디렉션됩니다.

<u>실제 결과</u>:

제품 목록 페이지로 리디렉션됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* Adobe Commerce 온-프레미스: 개발자 설명서에서 [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서 &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko) 섹션을 참조하십시오.
