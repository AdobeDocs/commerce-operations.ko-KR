---
title: 최종 확인
description: Adobe Commerce 애플리케이션에서 작동하도록 Varnish 구성이 제대로 설정되어 있는지 확인합니다.
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# 바니쉬 구성의 최종 확인

이제 을(를) 사용하고 있습니다. `default.vcl` Commerce에서 생성한 경우 Vannish가 작동하는지 확인하기 위해 몇 가지 최종 검증을 수행할 수 있습니다.

## HTTP 응답 헤더 확인

사용 `curl` 또는 웹 브라우저의 Commerce 페이지를 방문할 때 HTTP 응답 헤더를 보는 다른 유틸리티입니다.

먼저 다음을 사용하고 있는지 확인합니다. [개발자 모드](../cli/set-mode.md#change-to-developer-mode); 그렇지 않으면 헤더가 표시되지 않습니다.

예를 들어,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

중요 헤더:

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>이 값도 사용할 수 있습니다. `X-Magento-Cache-Debug: HIT`.

## 페이지 로드 시간 확인

바니시가 작동하는 경우 캐시 가능한 블록이 있는 모든 상거래 페이지는 150ms 이내에 로드되어야 합니다. 이러한 페이지의 예로는 현관 및 상점 카테고리 페이지가 있습니다.

브라우저 관리자를 사용하여 페이지 로드 시간을 측정합니다.

예를 들어 Chrome 관리자를 사용하려면 다음을 수행하십시오.

1. Chrome에서 캐시 가능한 상거래 페이지에 액세스합니다.
1. 페이지의 아무 곳이나 마우스 오른쪽 버튼으로 클릭합니다.
1. 팝업 메뉴에서 **[!UICONTROL Inspect Element]**
1. 검사기 창에서 **[!UICONTROL Network]** 탭.
1. 페이지를 새로 고칩니다.
1. 보고 있는 페이지의 URL을 볼 수 있도록 관리자 창의 맨 위로 스크롤합니다.

   다음 그림은 를 로드하는 예입니다 `magento2` 색인 페이지.

   ![보고 있는 페이지를 클릭합니다](../../assets/configuration/varnish-inspector.png)

   페이지 URL 옆에 페이지 로드 시간이 표시됩니다. 이 경우, 로드 시간은 5 ms이다. 이렇게 하면 Vannish가 페이지를 캐시했는지 확인하는 데 도움이 됩니다.

1. HTTP 응답 헤더를 보려면 페이지 URL(이름 열)을 누릅니다.

   HTTP 응답 헤더 확인 섹션에서 자세히 설명하는 HTTP 헤더를 볼 수 있습니다.

## 상거래 캐시 확인

다음을 확인합니다. `<magento_root>/var/page_cache` 디렉터리가 비어 있습니다.

1. Commerce 서버에 로그인하거나 파일 시스템 소유자로 전환합니다.
1. 다음 명령을 입력합니다.

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 하나 이상의 캐시 가능한 상거래 페이지에 액세스합니다.
1. 다음 확인: `var/page_cache/` 디렉토리.

   디렉터리가 비어 있으면 축하합니다! Varnish와 Commerce가 함께 작동하도록 구성했습니다!

1. 을(를) 지운 경우 `var/page_cache/` 디렉토리, 바니쉬 재시작

>[!TIP]
>
>503(백엔드 가져오기 실패) 오류가 발생하는 경우 다음을 참조하십시오. [503(서비스를 사용할 수 없음) 오류 문제 해결](https://support.magento.com/hc/en-us/articles/360034631211) 다음에서 _Adobe Commerce 도움말 센터_.
