---
title: '우선 순위가 다른 여러 할인을 적용할 때 ACSD-61553: [!UICONTROL Cart Price Rule]이(가) 잘못 계산됨'
description: 우선 순위가 다른 여러 할인을 적용할 때 [!UICONTROL Cart Price Rule]이(가) 잘못 계산되는 Adobe Commerce 문제를 해결하려면 ACSD-61553 패치를 적용하십시오.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# 우선 순위가 다른 여러 할인을 적용할 때 ACSD-61553: [!UICONTROL Cart Price Rule]이(가) 잘못 계산됨

ACSD-61553 패치는 우선 순위가 다른 여러 할인을 적용할 때 [!UICONTROL Cart Price Rule]이(가) 잘못 계산되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61553입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.5-p8

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

우선 순위가 다른 여러 할인 적용 시 [!UICONTROL Cart Price Rule]이(가) 잘못 계산됩니다.

<u>재현 단계</u>:

1. $9,000의 간단한 제품을 만들 수 있습니다.
1. [!UICONTROL Cart Price Rule]: 조건 없이 그리고 후속 규칙을 삭제하지 않고 고정 할인율 $700을 사용한 규칙 A를 만듭니다.
1. 다른 [!UICONTROL Cart Price Rule]: 조건 없이 후속 규칙을 삭제하지 않고 고정 할인율 $1,000을 사용한 규칙 B를 만듭니다.
1. 수량이 13인 제품을 장바구니에 추가합니다.
1. 아래 시나리오 중 하나로 규칙을 업데이트합니다.

   시나리오 01

       규칙 A
       우선 순위: 1
       최대 할인 대상: 1
       
       규칙 B
       우선 순위: 0
       최대 할인 대상: 0
   
   시나리오 02

       규칙 A
       우선 순위: 0
       최대 할인 대상: 0
       
       규칙 B
       우선 순위: 1
       최대 할인 대상: 1
   
   시나리오 03

       규칙 A
       우선 순위: 0
       최대 할인 대상: 0
       
       규칙 B
       우선 순위: 0
       최대 할인 대상: 1
   
1. **[!UICONTROL Update Shopping Cart]** 단추를 클릭하여 할인을 다시 계산합니다.

<u>예상 결과</u>:

다양한 시나리오에 대해 다음과 같은 총 할인이 표시됩니다.

    시나리오 01: $13,700
    시나리오 02: $10,100
    시나리오 03: $10,100

<u>실제 결과</u>:

세 가지 시나리오 모두 총 할인액은 9,000달러이다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
