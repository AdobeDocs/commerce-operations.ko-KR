---
title: 최종 확인
description: Adobe Commerce을 사용하여 Vanish 구성을 최종 확인하는 방법을 알아봅니다. 테스트 단계 및 문제 해결 기술을 살펴보십시오.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 바니쉬 구성의 최종 확인

이제 Commerce에서 생성한 `default.vcl`을(를) 사용하고 있으므로 Varnish가 작동하는지 최종 확인할 수 있습니다.

## HTTP 응답 헤더 확인

웹 브라우저의 Commerce 페이지를 방문할 때 `curl` 또는 다른 유틸리티를 사용하여 HTTP 응답 헤더를 봅니다.

먼저 [개발자 모드](../cli/set-mode.md#change-to-developer-mode)를 사용하고 있는지 확인하십시오. 그렇지 않으면 헤더가 표시되지 않습니다.

For example,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

중요 헤더:

```
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>이 값도 사용할 수 있습니다. `X-Magento-Cache-Debug: HIT`

## 페이지 로드 시간 확인

바니시가 작동하는 경우 캐시 가능한 블록이 있는 모든 Commerce 페이지는 150ms 이내에 로드되어야 합니다. 이러한 페이지의 예로는 현관 및 상점 카테고리 페이지가 있습니다.

브라우저 관리자를 사용하여 페이지 로드 시간을 측정합니다.

예를 들어 Chrome 관리자를 사용하려면 다음을 수행하십시오.

1. Chrome에서 캐시 가능한 Commerce 페이지에 액세스합니다.
1. 페이지의 아무 곳이나 마우스 오른쪽 버튼으로 클릭합니다.
1. 팝업 메뉴에서 **[!UICONTROL Inspect Element]**&#x200B;을(를) 클릭합니다.
1. 관리자 창에서 **[!UICONTROL Network]** 탭을 클릭합니다.
1. 페이지를 새로 고칩니다.
1. 보고 있는 페이지의 URL을 볼 수 있도록 관리자 창의 맨 위로 스크롤합니다.

   다음 그림은 `magento2` 인덱스 페이지를 로드하는 예입니다.

   ![보고 있는 페이지 클릭](../../assets/configuration/varnish-inspector.png)

   페이지 URL 옆에 페이지 로드 시간이 표시됩니다. 이 경우, 로드 시간은 5 ms이다. 이렇게 하면 Vannish가 페이지를 캐시했는지 확인하는 데 도움이 됩니다.

1. HTTP 응답 헤더를 보려면 페이지 URL(이름 열)을 누릅니다.

   HTTP 응답 헤더 확인 섹션에서 자세히 설명하는 HTTP 헤더를 볼 수 있습니다.

## Commerce 캐시 확인

`<magento_root>/var/page_cache` 디렉터리가 비어 있는지 확인합니다.

1. Commerce 서버에 로그인하거나 파일 시스템 소유자로 전환합니다.
1. 다음 명령을 입력합니다.

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 하나 이상의 캐시 가능한 Commerce 페이지에 액세스합니다.
1. `var/page_cache/` 디렉터리를 확인합니다.

   디렉터리가 비어 있으면 축하합니다! Varnish와 Commerce이 함께 작동하도록 구성했습니다!

1. `var/page_cache/` 디렉터리를 지운 경우 Varnish를 다시 시작합니다.

>[!TIP]
>
>503(백 엔드 가져오기 실패) 오류가 발생하면 [Adobe Commerce 도움말 센터](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html)에서 _503(서비스를 사용할 수 없음) 오류 문제 해결_&#x200B;을 참조하십시오.
