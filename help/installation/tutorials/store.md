---
title: 저장소 구성
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 스토어를 구성하십시오.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# 저장소 구성

이 명령을 실행하기 전에 다음을 수행해야 합니다 *또는* 반드시 [애플리케이션 설치](../advanced.md):

* [배포 구성 만들기 또는 업데이트](deployment.md)
* [데이터베이스 스키마 만들기](database.md)

## 보안 설치

{{$include /help/_includes/secure-install.md}}

## 저장소 구성

명령 사용:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

여기서 다음 표에서 매개 변수와 값을 정의합니다.

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--base-url` | 다음 형식으로 관리자 및 저장소에 액세스하는 데 사용할 기본 URL입니다.<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**참고:** 스키마(`http://` 또는 `https://`)과 후행 슬래시가 모두 필요합니다. `<your install dir>` 은 응용 프로그램을 설치할 docroot 상대 경로입니다. 웹 서버와 가상 호스트를 설정하는 방법에 따라 경로가 magento2일 수도 있고 비어 있을 수도 있습니다.<br><br>localhost에서 응용 프로그램에 액세스하려면 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 가상 호스트 설정에 의해 정의되거나 Docker와 같은 가상화 환경에 의해 정의된 기본 URL을 나타냅니다. 예를 들어 hostname commerce.example.com을 사용하여 가상 호스트를 설정하는 경우 `--base-url={{base_url}}` 와 같은 URL을 사용하여 관리자에 액세스합니다 `http://commerce.example.com/admin`. | 아니요 |
| `--language` | 관리자 및 스토어에 사용할 언어 코드입니다.<br><br>(아직 완료하지 않았다면 다음을 입력하여 언어 코드 목록을 볼 수 있습니다.) `magento info:language:list` 에서 `bin` 디렉토리). | 아니요 |
| `--currency` | 스토어에 사용할 기본 통화입니다. <br><br>(아직 수행하지 않았다면 다음을 입력하여 통화 목록을 볼 수 있습니다.) `magento info:currency:list` 에서 `bin` 디렉토리). | 아니요 |
| `--timezone` | 관리자 및 저장소 창에서 사용할 기본 시간대입니다. (아직 수행하지 않았다면 을 입력하여 시간대 목록을 볼 수 있습니다. `magento info:timezone:list` 에서 `bin` 디렉토리). | 아니요 |
| `--use-rewrites` | `1` 즉, 상점 및 관리자에서 생성된 링크에 웹 서버 rewrites를 사용합니다.<br><br>`0` 웹 서버 rewrites 사용을 비활성화합니다. 기본값입니다. | 아니요 |
| `--use-secure` | `1` 저장소 URL에서 SSL(Secure Sockets Layer)을 사용할 수 있습니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0` SSL 사용을 비활성화합니다. 이 경우 다른 모든 보안 URL 옵션도 0으로 간주됩니다. 기본값입니다. | 아니요 |
| `--base-url-secure` | 관리자 및 저장소에 액세스하는 데 사용할 보안 기본 URL로 다음 형식으로 저장됩니다. `http[s]://<host or ip>/<your install dir>/` | 아니요 |
| `--use-secure-admin` | `1` 는 SSL을 사용하여 관리자에 액세스함을 의미합니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0` 은 사용자가 관리자에 SSL을 사용하지 않음을 의미합니다. 기본값입니다. | 아니요 |
| `--admin-use-security-key` | `1` 애플리케이션이 임의로 생성된 키 값을 사용하여 관리자 및 양식의 페이지에 액세스하게 합니다. 이러한 주요 값은 사이트 간 스크립트 위조 공격을 방지하는 데 도움이 됩니다. 기본값입니다.<br/><br/>`0` 키 사용을 비활성화합니다. | 아니요 |
| `--magento-init-params` | 명령에 추가하여 응용 프로그램 초기화 매개변수를 사용자 정의합니다.<br/><br/>예: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 아니요 |
