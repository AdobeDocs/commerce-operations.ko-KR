---
title: 'ACSD-58141: PHPSESSID는 L2 Redis 캐시가 활성화된 로그인 고객에 대한 POST 요청 시 재생성합니다.'
description: ACSD-58141 패치를 적용하여 L2 Redis 캐시가 활성화된 로그인한 고객에 대해 'PHPSESSID'가 상점 첫 번째 영역의 POST 요청에서 재생성되고 고객이 관리자로부터 업데이트되는 Adobe Commerce 문제를 수정하십시오.
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-58141: L2 Redis 캐시가 활성화된 경우 로그인한 고객에 대한 [!DNL POST]개 요청에 대해 PHPSESSID가 다시 생성됩니다.

ACSD-58141 패치는 L2 Redis 캐시가 활성화되어 있고 고객이 Admin에서 업데이트된 경우 로그인한 고객에 대한 `PHPSESSID`개의 요청에서 [!DNL POST]이(가) 다시 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58141입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 및 Magento Open Source 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`PHPSESSID`은(는) L2 Redis 캐시가 활성화된 로그인 고객에 대한 [!DNL POST]개의 요청을 다시 생성합니다.

<u>필수 구성 요소</u>

최소 3개의 노드가 있는 Redis로 환경을 구성해야 합니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 고객을 만들고 Storefront에 로그인합니다.
1. `PHPSESSID`의 값을 확인합니다.
1. 몇 가지 [!DNL POST]개의 요청을 보냅니다(예: 장바구니에 제품 추가). `PHPSESSID`이(가) 동일하게 유지되는지 확인하십시오.
1. **[!UICONTROL Admin]** 패널에 로그인하고 고객의 가운데 이름을 변경합니다.
1. 가운데 이름이 저장되면 변경한 후 다시 몇 번 저장합니다.
1. 상점 첫 화면에서 [!DNL POST] 요청을 보냅니다. `PHPSESSID`을(를) 업데이트해야 합니다.
1. 상점 첫 화면에서 다른 [!DNL POST] 요청을 보내고 `PHPSESSID`을(를) 확인합니다.
1. 이전 단계를 몇 번 반복합니다.

<u>예상 결과</u>

고객 데이터를 변경한 후 `PHPSESSID`이(가) 한 번만 다시 생성됩니다.

<u>실제 결과</u>:

`PHPSESSID` 요청이 전송될 때마다 [!DNL POST]이(가) 다시 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
