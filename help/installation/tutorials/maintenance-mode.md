---
title: 유지 관리 모드 활성화 또는 비활성화
description: 유지 관리를 위해 Adobe Commerce 또는 Magento Open Source 배포가 중단될 때 고객이 볼 수 있는 내용을 사용자 지정하려면 다음 단계를 따르십시오.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 유지 관리 모드 활성화 또는 비활성화

다음 안내서는 표준 유지 관리 모드 페이지를 참조합니다. 사용자 지정 유지 관리 페이지를 사용해야 하는 경우 [사용자 지정 유지 관리 페이지 만들기](../../upgrade/troubleshooting/maintenance-mode-options.md) 주제.

Adobe Commerce 사용 [유지 관리 모드](../../configuration/bootstrap/application-modes.md#maintenance-mode) 부트스트래핑을 비활성화합니다. 부트스트래핑을 비활성화하는 것은 사이트를 유지 관리, 업그레이드 또는 재구성하는 동안 유용합니다.

애플리케이션은 다음과 같이 유지 관리 모드를 감지합니다.

* If `var/.maintenance.flag` 이(가) 없으며 유지 관리 모드가 꺼져 있고 응용 프로그램이 정상적으로 작동합니다.
* 그렇지 않으면 유지 관리 모드는 `var/.maintenance.ip` 존재함.

  `var/.maintenance.ip` 에는 IP 주소 목록이 포함될 수 있습니다. HTTP를 사용하여 진입점에 액세스하고 클라이언트 IP 주소가 해당 목록의 항목 중 하나에 해당하는 경우 유지 관리 모드는 해제됩니다.

## 애플리케이션 설치

이 명령을 사용하여 유지 관리 모드를 활성화하거나 비활성화하려면 먼저 다음을 수행해야 합니다 [응용 프로그램 설치](../advanced.md).

## 유지 관리 모드 활성화 또는 비활성화

사용 `magento maintenance` 유지 관리 모드를 설정하거나 해제하는 CLI 명령.

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

다음 `--ip=<ip address>` 옵션은 유지 관리 모드에서 제외할 IP 주소입니다(예: 유지 관리를 수행하는 개발자). 동일한 명령에서 두 개 이상의 IP 주소를 제외하려면 옵션을 여러 번 사용합니다.

>[!NOTE]
>
>사용 `--ip=<ip address>` 포함 `magento maintenance:disable` 나중에 사용할 수 있도록 IP 목록을 저장합니다. 제외 IP 목록을 지우려면 다음을 사용합니다. `magento maintenance:enable --ip=none` 또는 [제외 IP 주소 목록 유지](#maintain-the-list-of-exempt-ip-addresses).

다음 `bin/magento maintenance:status` 명령은 유지 관리 모드의 상태를 표시합니다.

예를 들어 IP 주소 면제가 없는 유지 관리 모드를 활성화하려면 다음을 수행합니다.

```bash
bin/magento maintenance:enable
```

192.0.2.10 및 192.0.2.11을 제외한 모든 클라이언트에 대해 유지 관리 모드를 활성화하려면 다음을 수행하십시오.

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

응용 프로그램을 유지 관리 모드로 설정한 후에는 모든 메시지 대기열 소비자 프로세스를 중지해야 합니다.
이러한 프로세스를 찾는 한 가지 방법은 `ps -ef | grep queue:consumers:start` 명령을 실행한 다음 `kill <process_id>` 각 소비자에 대한 명령입니다. 여러 노드 환경에서 각 노드에서 이 작업을 반복합니다.

## 제외 IP 주소 목록 유지

제외 IP 주소 목록을 유지 관리하려면 `[--ip=<ip list>]` 위의 명령에서 옵션을 선택하거나 다음을 사용할 수 있습니다.

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

다음 `<ip address> .. <ip address>` 구문은 제외할 IP 주소의 선택적 공백으로 구분된 목록입니다.

다음 `--none` 옵션은 목록을 지웁니다.

## 다중 스토어 설정

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

각각 다른 레이아웃과 현지화된 콘텐츠가 있는 여러 스토어를 설정하려면 `$_GET['skin']` 원하는 프로세서에 대한 매개 변수입니다.

다음 예제에서는 `503` 형식 오류 템플릿 파일입니다. 이 파일의 경우 지역화된 내용이 필요합니다.

의 생성자입니다. `Error_Processor` 클래스에서 다음을 수락합니다. `skin` 레이아웃을 변경할 GET 매개 변수:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

의 다시 작성 규칙에 추가할 수도 있습니다. `.htaccess` 를 추가하는 파일 `skin` 매개 변수를 URL에 추가합니다.

### $_GET[&#39;스킨&#39;] 매개 변수

을(를) 사용하려면 `skin` 매개 변수:

1. 다음을 확인함: `.maintenance.flag` 존재함.
1. 를 참조하는 호스트 주소를 확인합니다. `HTTP_HOST`또는 ENV 변수와 같은 기타 모든 변수입니다.
1. 다음을 확인함: `skin` 매개 변수가 있습니다.
1. 아래 재작성 규칙을 사용하여 매개 변수를 설정합니다.

   다음은 규칙 다시 작성의 몇 가지 예입니다.

   * 콘드 다시 작성 `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * 콘드 다시 작성 `%{HTTP_HOST} ^sub.example.com$`
   * 콘드 다시 작성 `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * 규칙 다시 작성 `^ %{REQUEST_URI}?skin=sub` [L]

1. 다음 파일을 복사합니다.

   * `pub/errors/default/503.phtml` 끝 `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` 끝 `pub/errors/sub/styles.css`

1. 에서 현지화된 콘텐츠를 제공하도록 이러한 파일을 편집합니다. `503.phtml` 파일 및 사용자 지정 스타일 `styles.css` 파일.

   경로가 을(를) 가리키는지 확인합니다. `errors` 디렉토리. 디렉터리 이름은 다음에 표시된 URL 매개 변수와 일치해야 합니다 `RewriteRule`. 앞의 예제에서는 `sub` 디렉토리가 사용되며, 이 디렉토리는 의 매개변수로 지정됩니다. `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>다음 [nginx](../../configuration/multi-sites/ms-nginx.md) 다중 스토어 설정에 대한 설정을 추가해야 합니다.
