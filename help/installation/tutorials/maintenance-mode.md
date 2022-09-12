---
title: 유지 관리 모드 활성화 또는 비활성화
description: 다음 단계에 따라 유지 관리를 위해 Adobe Commerce 또는 Magento Open Source 배포이 다운될 때 고객이 보게 되는 내용을 사용자 지정합니다.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---


# 유지 관리 모드 활성화 또는 비활성화

다음 안내서는 표준 유지 관리 모드 페이지를 참조합니다. 사용자 지정 유지 관리 페이지를 사용해야 하는 경우 [사용자 지정 유지 관리 페이지 만들기](../../upgrade/troubleshooting/maintenance-mode-options.md) 주제.

Adobe Commerce 및 Magento Open Source 사용 [유지 모드](../../configuration/bootstrap/application-modes.md#maintenance-mode) 부트스트래핑 사용 안 함 부트스트래핑 비활성화는 사이트를 유지 관리, 업그레이드 또는 재구성하는 동안 유용합니다.

애플리케이션은 다음과 같이 유지 관리 모드를 감지합니다.

* If `var/.maintenance.flag` 가 존재하지 않으면 유지 관리 모드가 해제되고 애플리케이션이 정상적으로 작동합니다.
* 그렇지 않으면 유지 관리 모드가 `var/.maintenance.ip` 존재함.

   `var/.maintenance.ip` 에는 IP 주소 목록이 포함될 수 있습니다. HTTP를 사용하여 진입점에 액세스하는 경우 클라이언트 IP 주소가 해당 목록의 항목 중 하나에 해당하는 경우 유지 관리 모드가 해제됩니다.

## 응용 프로그램 설치

이 명령을 사용하여 유지 관리 모드를 활성화 또는 비활성화하려면 먼저 [애플리케이션 설치](../advanced.md).

## 유지 관리 모드 활성화 또는 비활성화

를 사용하십시오 `magento maintenance` 유지 관리 모드를 활성화하거나 비활성화하는 CLI 명령

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

다음 `--ip=<ip address>` option은 유지 관리 모드에서 제외되는 IP 주소입니다(예: 유지 관리를 수행하는 개발자). 동일한 명령에서 두 개 이상의 IP 주소를 제외하려면 옵션을 여러 번 사용합니다.

>[!NOTE]
>
>사용 `--ip=<ip address>` with `magento maintenance:disable` 나중에 사용할 수 있도록 IP 목록을 저장합니다. 제외 IP 목록을 지우려면 `magento maintenance:enable --ip=none` 또는 [제외 IP 주소 목록 유지](#maintain-the-list-of-exempt-ip-addresses).

다음 `bin/magento maintenance:status` 명령은 유지 관리 모드의 상태를 표시합니다.

예를 들어, IP 주소 면제 없이 유지 관리 모드를 활성화하려면

```bash
bin/magento maintenance:enable
```

192.0.2.10 및 192.0.2.11을 제외한 모든 클라이언트에 대해 유지 관리 모드를 사용하려면

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

응용 프로그램을 유지 관리 모드로 전환한 후에는 모든 메시지 큐 소비자 프로세스를 중지해야 합니다.
이러한 프로세스를 찾는 한 가지 방법은 `ps -ef | grep queue:consumers:start` 명령을 실행한 다음 `kill <process_id>` 각 소비자에 대한 명령. 여러 노드 환경에서 각 노드에서 이 작업을 반복합니다.

## 제외 IP 주소 목록 유지

제외 IP 주소 목록을 유지 관리하려면 `[--ip=<ip list>]` 이전 명령에서 옵션을 선택하거나 다음을 사용할 수 있습니다.

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

다음 `<ip address> .. <ip address>` 구문은 제외할 IP 주소의 선택적 공간 구분 목록입니다.

다음 `--none` 옵션을 선택하면 목록이 지워집니다.

## 다중 저장소 설정

각각 다른 레이아웃과 현지화된 컨텐츠가 있는 여러 스토어를 설정하려면 각 스토어마다 스킨을 만들어 `pub/errors/{name}` 여기서 `{name}` 는 스토어 코드입니다. 동일한 인스턴스를 사용하여 스토어와 웹 사이트를 구분하려면 를 사용하십시오 `pub/errors/{type}-{name}` 여기서 `{type}` 다음 중 하나입니다. `store` 또는 `website` 및 가 `MAGE_RUN_TYPE` ( 서버 구성에 있음)을 참조하십시오.

다른 옵션은 를 전달하는 것입니다 `$_GET['skin']` 매개 변수를 사용하십시오. 이 메서드는 서버에 특정 구성이 필요합니다.

다음 예에서는 `503` 오류 템플릿 파일 입력. 현지화된 콘텐츠가 필요합니다.

의 생성자입니다. `Error_Processor` 클래스는 `skin` GET 매개 변수를 사용하여 레이아웃을 변경합니다.

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

또한, 이 값은 의 rewrite 규칙에 추가할 수 있습니다 `.htaccess` 추가할 파일 `skin` 매개 변수를 URL에 추가합니다.

### $_GET[&#39;skin&#39;] 매개 변수

를 사용하려면 `skin` 매개 변수:

1. 다음을 확인하십시오. `.maintenance.flag` 존재함.
1. 호스트 주소( `HTTP_HOST`또는 ENV 변수와 같은 기타 모든 변수.
1. 다음을 확인하십시오. `skin` 매개 변수가 있습니다.
1. 아래 rewrite 규칙을 사용하여 매개 변수를 설정합니다.

   다음은 재작성 규칙의 예입니다.

   * RewriteCode `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCode `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCode `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 다음 파일을 복사합니다.

   * `pub/errors/default/503.phtml` to `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` to `pub/errors/sub/styles.css`

1. 이러한 파일을 편집하여 `503.phtml` 파일 및 사용자 정의 스타일링 `styles.css` 파일.

   경로가 `errors` 디렉토리. 디렉토리 이름은 `RewriteRule`. 이전 예에서 `sub` 디렉토리는 `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>다음 [nginx](../../configuration/multi-sites/ms-nginx.md) 다중 저장소 설정에 대한 설정을 추가해야 합니다.
