---
title: 캐시 중독 방지
description: Commerce Store에 대한 페이지 캐시 중독을 방지하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# 캐시 중독 방지

이 항목에서는 다음을 방지하는 방법을 설명합니다 [캐시](https://glossary.magento.com/cache) Microsoft IIS(인터넷 정보 서버) 웹 서버를 사용하는 경우 중독 _캐시 중독_ 은 동일한 사이트의 다른 페이지를 포함하도록 캐시 콘텐츠를 변경하는 방법입니다. 예를 들어 일부 양성 페이지(예: [상점](https://glossary.magento.com/storefront) 홈 페이지)로 설정될 수도 있습니다. 악성 페이지 URL은 Varnish 또는 Redis에 의해 캐시되므로 이름이 됩니다 _페이지 캐시 중독_.

이러한 유형의 공격은 웹 서버 로그에 오류가 발생하지 않으므로 검색하기 어려울 수 있습니다.

이 솔루션은 다음 상거래 버전에 적용됩니다.

- 2.0.10 이상
- 2.1.2 이상

>[!INFO]
>
>이 항목은 숙련된 IIS 관리자를 위한 것입니다.

## 설명

이 문제는 IIS 서버에서 URL 다시 쓰기가 활성화되고 요청이 Varnish 또는 Redis 캐싱 서비스에 도달하기 전에 다음 HTTP 헤더가 변경되는 경우 발생합니다.

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

이러한 헤더가 변경되면 결과 URL 및 콘텐츠가 캐시되어 잠재적 취약점이 발생합니다.

## 솔루션

IIS 서버 설정에 따라 이전 헤더의 모든 값을 제거하는 옵션을 제공합니다. `Enable_IIS_Rewrites`.

- If `Enable_IIS_Rewrites` 가 로 설정되어 있습니다. `0`이면 헤더 값이 제거됩니다.
- If `Enable_IIS_Rewrites` 가 로 설정되어 있습니다. `1`헤더 값은 그대로 유지됩니다.

>[!WARNING]
>
>설정 `Enable_IIS_Rewrites` to `1`를 지정하면, 요청이 IIS 웹 서버에 도달하기 전에 이전 헤더의 값을 변경할 수 없습니다.
