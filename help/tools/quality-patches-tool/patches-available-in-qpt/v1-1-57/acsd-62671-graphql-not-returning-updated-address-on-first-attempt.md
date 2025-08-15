---
title: 'ACSD-62671: [!DNL GraphQL] 첫 번째 시도에서 업데이트된 주소를 반환하지 않습니다.'
description: ACSD-62671 패치를 적용하여  [!DNL GraphQL] 요청이 첫 번째 시도에서 최신 주소 정보를 반환하지 않는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL]이(가) 첫 번째 시도에서 업데이트된 주소를 반환하지 않습니다.

ACSD-62671 패치는 [!DNL GraphQL] 요청이 첫 번째 시도에서 최신 주소 정보를 반환하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62671입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL GraphQL Application Server]을(를) 사용하는 경우 고객 주소 요청은 최신 데이터를 반환하지 않습니다.

<u>재현 단계</u>:

1. [!DNL GraphQL Application Server]을(를) 설치하고 시작합니다.
1. `graphQL_query_resolver_result` 캐시 형식이 활성화되어 있는지 확인합니다.
1. [!DNL GraphQL]을(를) 사용하여 다음을 수행합니다.

   * 고객을 만듭니다.
   * 토큰을 생성합니다.
   * 위의 고객을 위한 여러 주소를 만들려면 토큰을 사용하십시오.

1. 고객의 주소를 가져오려면 [!DNL GraphQL] 요청을 보냅니다.
1. 고객에 새 주소를 추가합니다.
1. 응답에서 반환된 주소 수를 모니터링하는 동안 #4단계의 요청을 여러 번 반복합니다.

<u>예상 결과</u>:

[!DNL GraphQL] 응답에 올바른 수의 고객 주소가 포함되어 있습니다.

<u>실제 결과</u>:

[!DNL GraphQL] 응답에서 잘못된 주소 수가 반환되는 경우가 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
