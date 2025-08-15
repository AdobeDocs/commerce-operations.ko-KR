---
title: 유지 관리 모드 활성화 또는 비활성화
description: 유지 관리를 위해 Adobe Commerce 배포가 중단될 때 고객이 볼 수 있는 내용을 사용자 지정하려면 다음 단계를 따르십시오.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# 유지 관리 모드 활성화 또는 비활성화

다음 안내서는 표준 유지 관리 모드 페이지를 참조합니다. 사용자 지정 유지 관리 페이지를 사용해야 하는 경우 [사용자 지정 유지 관리 페이지 만들기](../../upgrade/troubleshooting/maintenance-mode-options.md) 항목을 참조하십시오.

Adobe Commerce은 [유지 관리 모드](../../configuration/bootstrap/application-modes.md#maintenance-mode)를 사용하여 부트스트래핑을 비활성화합니다. 부트스트래핑을 비활성화하는 것은 사이트를 유지 관리, 업그레이드 또는 재구성하는 동안 유용합니다.

애플리케이션은 다음과 같이 유지 관리 모드를 감지합니다.

* `var/.maintenance.flag`이(가) 있으면 유지 관리 모드가 켜져 있으며 응용 프로그램에서 503 유지 관리 페이지를 반환합니다.
* `var/.maintenance.ip`이(가) 있고 클라이언트 IP가 이 파일 내의 IP 주소 항목 중 하나에 해당하는 경우 요청에 대한 유지 관리 페이지가 무시됩니다.

## 애플리케이션 설치

이 명령을 사용하여 유지 관리 모드를 활성화하거나 비활성화하려면 먼저 [응용 프로그램을 설치](../advanced.md)해야 합니다.

## 유지 관리 모드 활성화 또는 비활성화

유지 관리 모드를 활성화하거나 비활성화하려면 `magento maintenance` CLI 명령을 사용하십시오.

명령 사용:

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

`--ip=<ip address>` 옵션은 유지 관리 모드에서 제외할 IP 주소입니다(예: 유지 관리를 수행하는 개발자). 동일한 명령에서 두 개 이상의 IP 주소를 제외하려면 옵션을 여러 번 사용합니다.

>[!NOTE]
>
>`--ip=<ip address>`을(를) `magento maintenance:disable`과(와) 함께 사용하면 나중에 사용할 수 있도록 IP 목록이 저장됩니다. 제외 IP 목록을 지우려면 `magento maintenance:enable --ip=none`을(를) 사용하거나 [제외 IP 주소 목록 유지](#maintain-the-list-of-exempt-ip-addresses)를 참조하십시오.

`bin/magento maintenance:status` 명령은 유지 관리 모드의 상태를 표시합니다.

예를 들어 IP 주소 면제가 없는 유지 관리 모드를 활성화하려면 다음을 수행합니다.

```bash
bin/magento maintenance:enable
```

192.0.2.10 및 192.0.2.11을(를) 제외한 모든 클라이언트에 대한 유지 관리 모드를 활성화하려면:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

응용 프로그램을 유지 관리 모드로 설정한 후에는 모든 메시지 대기열 소비자 프로세스를 중지해야 합니다.
이러한 프로세스를 찾는 한 가지 방법은 `ps -ef | grep queue:consumers:start` 명령을 실행한 다음 각 소비자에 대해 `kill <process_id>` 명령을 실행하는 것입니다. 여러 노드 환경에서 각 노드에서 이 작업을 반복합니다.

## 제외 IP 주소 목록 유지

제외 IP 주소 목록을 유지 관리하기 위해 이전 명령에서 `[--ip=<ip list>]` 옵션을 사용하거나 다음을 사용할 수 있습니다.

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

`<ip address> .. <ip address>` 구문은 제외할 공백으로 구분된 선택적 IP 주소 목록입니다.

`--none` 옵션은 목록을 지웁니다.

## 다중 스토어 설정

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

각각 다른 레이아웃과 현지화된 콘텐츠를 가진 여러 저장소를 설정하려면 원하는 프로세서에 `$_GET['skin']` 매개 변수를 전달하십시오.

다음 예제에서는 현지화된 콘텐츠가 필요한 `503` 형식 오류 템플릿 파일을 사용하고 있습니다.

`Error_Processor` 클래스의 생성자가 `skin` GET 매개 변수를 사용하여 레이아웃을 변경할 수 있습니다.

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

URL에 `.htaccess` 매개 변수를 추가하는 `skin` 파일의 다시 작성 규칙에도 추가할 수 있습니다.

### $_GET[&#39;skin&#39;] 매개 변수

`skin` 매개 변수를 사용하려면:

1. `.maintenance.flag`이(가) 있는지 확인하십시오.
1. `HTTP_HOST`을(를) 참조하는 호스트 주소 또는 ENV 변수와 같은 다른 변수를 확인합니다.
1. `skin` 매개 변수가 있는지 확인하십시오.
1. 아래 재작성 규칙을 사용하여 매개 변수를 설정합니다.

   다음은 규칙 다시 작성의 몇 가지 예입니다.

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 다음 파일을 복사합니다.

   * `pub/errors/default/503.phtml` - `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` - `pub/errors/sub/styles.css`

1. `503.phtml` 파일의 지역화된 콘텐츠와 `styles.css` 파일의 사용자 지정 스타일을 제공하도록 이러한 파일을 편집하십시오.

   경로가 `errors` 디렉터리를 가리키는지 확인하십시오. 디렉터리 이름이 `RewriteRule`에 표시된 URL 매개 변수와 일치해야 합니다. 앞의 예제에서는 `sub`(`RewriteRule`)에 매개 변수로 지정된 `skin=sub` 디렉터리가 사용되었습니다.

>[!NOTE]
>
>다중 저장소 설정에 [nginx](../../configuration/multi-sites/ms-nginx.md) 설정을 추가해야 합니다.
