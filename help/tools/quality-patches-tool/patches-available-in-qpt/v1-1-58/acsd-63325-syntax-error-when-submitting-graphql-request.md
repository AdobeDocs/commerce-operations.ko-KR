---
title: 'ACSD-63325: 구문 오류: empty [!DNL GraphQL] 요청을 제출할 때 예기치 않은 &lt;EOF&gt; 오류가 발생했습니다.'
description: ACSD-63325 패치를 적용하여 빈  [!DNL GraphQL] 요청을 제출할 때 구문 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325: 빈 [!DNL GraphQL] 요청을 제출할 때 &quot;구문 오류: 예기치 않은 &lt; EOF >&quot; 오류 발생

ACSD-63325 패치는 빈 [!DNL GraphQL] 요청을 제출할 때 &quot;구문 오류: 예기치 않은 &lt; EOF >&quot; 오류 및 200이 아닌 응답 코드가 반환되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63325입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

빈 [!DNL GraphQL] 요청을 제출할 때 200 응답 코드 대신 HTTP 내부 서버 오류가 있습니다.

<u>재현 단계</u>:

1. 빈 GraphQL 요청 보내기

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>예상 결과</u>:

요청에 대한 응답 코드는 200입니다.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>실제 결과</u>:

아래와 같이 500 내부 서버 오류가 발생합니다.

```
HTTP/1.1 500 Internal Server Error
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
