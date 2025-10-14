---
title: 'ACSD-66952: 대상 규칙이 설정되면 캐시가 각 PLP 또는 장바구니 방문에서 지워짐'
description: ACSD-66952 패치를 적용하여 각 PLP 또는 장바구니 방문에서 캐시가 지워져 타겟 규칙이 설정될 때 불필요한 성능 오버헤드가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-66952: 대상 규칙이 설정되면 캐시가 각 PLP 또는 장바구니 방문에서 지워짐

ACSD-66952 패치는 각 PLP 또는 장바구니 방문에서 캐시가 지워져서 대상 규칙이 설정될 때 성능 오버헤드를 초래하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66952입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

각 PLP 또는 장바구니 방문에서 캐시가 지워져 타겟 규칙이 설정될 때 성능 오버헤드가 발생하는 문제입니다.

<u>재현 단계</u>:

1. 작은 샘플 데이터 세트를 생성합니다.
1. 다음과 같이 대상 규칙 값을 만듭니다.
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *관련 제품*
      * **[!UICONTROL Status]** = *활성*
      * **[!UICONTROL Apply to]** = *관련 제품*
   1. **[!UICONTROL Products to Match]**
      * 기본값으로 둡니다.
   1. **[!UICONTROL Products to Display]**
      * 이러한 조건 중 **모두**&#x200B;이(가) *true*&#x200B;인 경우 **[!UICONTROL Product Category]** = *상수 값 111111*&#x200B;을(를) 설정하십시오.
1. 캐시 무효화 요청에 대한 로그 모니터링을 시작합니다.
1. 제품 페이지를 방문합니다.
1. 장바구니에 제품을 추가하고 장바구니 페이지로 이동합니다.

<u>예상 결과</u>:

애플리케이션은 사이트를 탐색하는 동안 캐시를 무효화해서는 안 됩니다.

<u>실제 결과</u>:

캐시 태그가 무효화됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko)

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
