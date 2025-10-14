---
title: 'ACSD-49970: GraphQL 오류의 잘못된 처리'
description: ACSD-49970 패치를 적용하여 [!UICONTROL New Relic Reporting]이(가) 켜져 있을 때 GraphQL 오류를 잘못 처리하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970: GraphQL 오류의 잘못된 처리

ACSD-49970 패치는 *[!UICONTROL New Relic Reporting]*&#x200B;이(가) 켜져 있을 때 GraphQL 오류를 잘못 처리하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49970입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`GraphQLOperationNames`에 이 키가 포함되어 있는지 여부에 관계없이 `logDataHelper` 키가 올바르게 처리되지 않습니다.

<u>재현 단계</u>:

1. `bin/magento deploy:mode:set developer` 실행.
1. 관리자에 로그인합니다.
1. **[!UICONTROL New Relic Integration]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**&#x200B;에서 **[!UICONTROL New Relic Reporting]** 사용
(참고: [!DNL New Relic] 확장을 사용할 수 없다는 오류가 표시되더라도 구성이 저장됩니다.)
1. *클라이언트 또는 다른 클라이언트에서 또는 cURL을 통해*&#x200B;에 대해 이 `http://yourMagentoDomain/graphql`GraphQL *[!DNL Altair]* 돌연변이를 실행하십시오.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (참고: 실행하기 전에 **[!UICONTROL Header]**&#x200B;을(를) [!UICONTROL Content-Currency:CA]&#x200B;(으)로 설정합니다.)

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>예상 결과</u>:

로그에 *500 예외*&#x200B;이(가) 없습니다. `GraphQLOperationNames` 키가 올바르게 처리되고 있습니다.

<u>실제 결과</u>:

로그에 *500 예외*&#x200B;이(가) 있습니다. `GraphQLOperationNames` 키가 제대로 처리되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
