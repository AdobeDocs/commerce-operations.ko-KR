---
title: 캐시 중독 방지
description: Commerce 상점 첫 화면의 페이지 캐시 중독을 방지하는 방법에 대해 알아봅니다.
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 캐시 중독 방지

이 항목에서는 Microsoft IIS(인터넷 정보 서버) 웹 서버를 사용하는 경우 캐시 중독을 방지하는 방법에 대해 설명합니다. _캐시 중독_ 동일한 사이트의 다른 페이지를 포함하도록 캐시 콘텐츠를 변경하는 방법입니다. 예를 들어, 일부 양성 페이지(예: 상점 홈 페이지) 대신 HTTP 404(찾을 수 없음) 오류 페이지를 삽입할 수 있으므로 DoS(서비스 거부)가 발생할 수 있습니다. 악의적인 페이지 URL은 Varnish 또는 Redis에 의해 캐시됩니다. _페이지 캐시 중독_.

이러한 유형의 공격은 웹 서버 로그에 오류를 발생시키지 않으므로 감지하기 어려울 수 있습니다.

이 솔루션은 다음 Commerce 버전에 적용됩니다.

- 2.0.10 이상
- 2.1.2 이상

>[!INFO]
>
>이 항목은 숙련된 IIS 관리자를 위한 것입니다.

## 설명

이 문제는 IIS 서버에서 URL 재쓰기가 활성화되어 있고, 요청이 Varnish 또는 Redis 캐싱 서비스에 도달하기 전에 다음 HTTP 헤더 중 하나가 변경되는 경우 발생합니다.

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

이러한 헤더가 변경되면 결과 URL 및 콘텐츠가 캐시되어 잠재적인 취약점이 발생합니다.

## 솔루션

에 대한 IIS 서버 설정을 기반으로 이전 모든 헤더의 값을 제거하는 옵션을 제공합니다 `Enable_IIS_Rewrites`.

- If `Enable_IIS_Rewrites` 이(가) (으)로 설정됨 `0`, 헤더 값이 제거됩니다.
- If `Enable_IIS_Rewrites` 이(가) (으)로 설정됨 `1`, 머리글의 값은 그대로 유지됩니다.

>[!WARNING]
>
>다음을 설정하는 경우 `Enable_IIS_Rewrites` 끝 `1`, 요청이 IIS 웹 서버에 도달하기 전에 이전 헤더의 값을 변경할 수 없도록 해야 합니다.
