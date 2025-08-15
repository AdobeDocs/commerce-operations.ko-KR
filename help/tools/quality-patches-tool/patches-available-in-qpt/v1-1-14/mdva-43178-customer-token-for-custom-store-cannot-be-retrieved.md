---
title: 'MDVA-43178: GraphQL에서 사용자 지정 스토어에 대한 고객 토큰을 검색할 수 없습니다.'
description: MDVA-43178 패치는 GraphQL에서 사용자 지정 스토어에 대한 고객 토큰을 검색할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43178입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: GraphQL
role: Admin
exl-id: 8dd9c9e7-573c-4c7a-8fd0-3b3886649af3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-43178: GraphQL에서 사용자 지정 스토어에 대한 고객 토큰을 검색할 수 없습니다.

MDVA-43178 패치는 GraphQL에서 사용자 지정 스토어에 대한 고객 토큰을 검색할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43178입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL에서 사용자 지정 스토어에 대한 고객 토큰을 검색할 수 없습니다.

<u>재현 단계</u>:

1. 기본 스토어에 대해 두 개의 스토어 뷰를 만듭니다.
1. 새 웹 사이트, 스토어 및 스토어 보기를 만듭니다. 이 저장소 보기의 이름을 &#39;test3&#39;으로 지정합니다.
1. 새 웹 사이트에 대한 고객을 만듭니다.
1. API 관리 토큰 생성:

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    {
      "username": "login",
      "password": "password"
    }
    </code>
    </pre>

1. GraphQL을 전송하여 고객 토큰을 관리자로 검색하고 인증에 관리자 토큰을 사용합니다. 헤더에 &quot;store&quot; = &quot;test3&quot;을 사용합니다.

   <pre>
    <customer_email>
      </pre>

<u>예상 결과</u>:

고객 토큰이 생성됩니다.

<u>실제 결과</u>:

고객 토큰이 생성되지 않았습니다. 회신에 대해 가맹점이 *제공된 고객 전자 메일이 존재하지 않습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
