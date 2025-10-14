---
title: 'ACSD-63870: 회사 상태 변경 중에 고객이 제대로 로그아웃되지 않음'
description: ACSD-63870 패치를 적용하여 활성 고객 세션 중에 회사 상태가 변경될 때 회사 고객이 제대로 로그아웃되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870: 회사 상태 변경 중에 고객이 제대로 로그아웃되지 않음

ACSD-63870 패치는 활성 고객 세션 중에 회사 상태가 변경될 때 회사 고객이 제대로 로그아웃되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63870입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

활성 고객 세션 중에 회사 상태가 변경되면 고객 로그아웃 오류가 발생합니다.

<u>재현 단계</u>:

1. B2B 기능을 활성화합니다.
1. 간단한 제품을 만듭니다.
1. 새 회사를 만들고 *활성*(으)로 표시합니다.
1. 회사 사용자로 로그인하고 장바구니에 제품을 추가합니다.
1. [!UICONTROL Shipping Address] 단계까지 체크아웃을 진행합니다. 주소를 입력하지 마십시오.
1. 관리자로 이동하여 회사 상태를 *승인 보류 중*(으)로 변경합니다.
1. 프론트엔드로 돌아가서 배송 주소를 입력하십시오.

<u>예상 결과</u>:

고객이 로그아웃되었습니다.

<u>실제 결과</u>:

* *문제가 발생했습니다* 오류가 발생했습니다.
* `var/log/exception.log`에 포함된 항목:

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 패치 설치 후 추가 단계 필요

(이 섹션은 선택 사항입니다. 문제를 해결하기 위해 패치를 적용한 후 몇 가지 단계가 필요할 수 있습니다.) 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
