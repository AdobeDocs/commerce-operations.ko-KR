---
title: "ACSD-61845: text/html accept 헤더가 있는 요청에 대해 오류가 발생했습니다."
description: ACSD-61845 패치를 적용하여 *text/html* accept 헤더만 사용하여 HTTP 요청을 보내면 B2B 모듈이 설치된 상태에서 500 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: B2B
role: Admin, Developer
source-git-commit: 8dbf91806097281fb4f7c74e182f10b09b18e925
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: *text/html* accept 헤더가 있는 요청에 오류가 발생했습니다.

ACSD-61845 패치는 응답 처리에서 미디어 유형 불일치로 인해 *text/html* accept 헤더만 있는 HTTP 요청으로 인해 500 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61845입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

accept 헤더에 *text/html*&#x200B;만 있는 HTTP 요청을 보낼 때 미디어 유형 구성이 일치하지 않아 500 오류가 발생합니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되고 활성화됩니다.

<u>재현 단계</u>:

1. 다음과 같이 accept 헤더에 *text/html*&#x200B;만 있는 요청을 보냅니다.

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>예상 결과</u>:

페이지가 *200 상태 코드*&#x200B;와 함께 반환됩니다.

<u>실제 결과</u>:

500 오류가 반환되고 `exception.log`에 다음 오류 메시지가 표시됩니다.

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).