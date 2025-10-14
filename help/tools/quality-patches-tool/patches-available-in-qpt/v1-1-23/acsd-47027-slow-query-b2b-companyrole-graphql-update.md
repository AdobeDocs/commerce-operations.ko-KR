---
title: 'ACSD-47027: 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트'
description: ACSD-47027 패치를 적용하여 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트가 있는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027: 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트

ACSD-47027 패치는 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트가 예상대로 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47027입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트가 예상대로 작동하지 않습니다.

<u>필수 구성 요소</u>:

B2B 모듈을 설치합니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]**(으)로 이동하여 **[!UICONTROL Enable Company]**&#x200B;을(를) _예_(으)로 설정합니다.
1. 프론트엔드로 이동하여 회사를 만듭니다.
1. 회사 사용자로 로그인한 후 **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]**(으)로 이동하여 새 역할을 추가합니다.
1. [!UICONTROL dev]을(를) 사용하여 `bin/magento dev:que:enab` 쿼리 로그를 사용하도록 설정합니다.
1. 이제 아래 [!DNL GraphQL] 요청을 보냅니다(ID는 [!UICONTROL base64] 인코딩된 역할 ID).

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. 쿼리 로그를 확인합니다.
1. 위의 쿼리가 실행되었음을 알 수 있습니다. 이 쿼리는 `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`에서 실행됩니다.

<u>예상 결과</u>:

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` DB 테이블에서 사용 가능한 모든 데이터를 로드하지 않도록 **[!UICONTROL company_permissions]**&#x200B;을(를) 최적화해야 합니다.

<u>실제 결과</u>:

Adobe Commerce은 필터 없이 쿼리를 실행합니다. 기록이 많을 때는 Adobe Commerce이 데이터 수집을 준비하는 데 많은 시간이 걸린다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko). 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
