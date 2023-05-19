---
title: 스토어 구성
description: Adobe Commerce 또는 Magento Open Source 스토어를 구성하려면 다음 단계를 따르십시오.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# 스토어 구성

이 명령을 실행하기 전에 다음을 수행해야 합니다 *또는* 다음을 수행해야 합니다. [응용 프로그램 설치](../advanced.md):

* [배포 구성 만들기 또는 업데이트](deployment.md)
* [데이터베이스 스키마 만들기](database.md)

## 보안 설치

{{$include /help/_includes/secure-install.md}}

## 스토어 구성

명령 사용:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

여기서 다음 표는 매개 변수와 값을 정의합니다.

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--base-url` | 관리자 및 상점 첫 화면에 다음 형식 중 하나로 액세스하는 데 사용할 기본 URL:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**참고:** 체계 (`http://` 또는 `https://`) 및 후행 슬래시가 모두 필요합니다. `<your install dir>` 는 애플리케이션을 설치할 docroot 상대 경로입니다. 웹 서버와 가상 호스트를 설정하는 방법에 따라 경로가 magento2이거나 비어 있을 수 있습니다.<br><br>localhost에서 응용 프로그램에 액세스하려면 다음을 사용할 수 있습니다. `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 가상 호스트 설정 또는 Docker와 같은 가상화 환경으로 정의된 기본 URL을 나타냅니다. 예를 들어 호스트 이름 commerce.example.com 을 사용하여 가상 호스트를 설정하는 경우 `--base-url={{base_url}}` 과 같은 URL을 사용하여 관리자에 액세스 `http://commerce.example.com/admin`. | 아니요 |
| `--language` | 관리자 및 상점 첫 화면에서 사용할 언어 코드.<br><br>(아직 그렇게 하지 않은 경우 다음을 입력하여 언어 코드 목록을 볼 수 있습니다. `magento info:language:list` 다음에서 `bin` directory.) | 아니요 |
| `--currency` | 상점 첫 화면에서 사용할 기본 통화. <br><br>(아직 통화하지 않은 경우 다음을 입력하여 통화 목록을 볼 수 있습니다. `magento info:currency:list` 다음에서 `bin` directory.) | 아니요 |
| `--timezone` | 관리자 및 상점 첫 화면에서 사용할 기본 시간대. 아직 시간대를 입력하지 않은 경우 다음을 입력하여 시간대 목록을 볼 수 있습니다 `magento info:timezone:list` 다음에서 `bin` directory.) | 아니요 |
| `--use-rewrites` | `1` 은(는) storefront 및 Admin에서 생성된 링크에 대해 웹 서버 재작성을 사용함을 의미합니다.<br><br>`0` 웹 서버 재작성 사용을 비활성화합니다. 이것이 기본값입니다. | 아니요 |
| `--use-secure` | `1` storefront URL에서 SSL(Secure Sockets Layer)을 사용할 수 있도록 합니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0` ssl 사용을 비활성화합니다. 이 경우 다른 모든 보안 URL 옵션도 0이라고 가정합니다. 이것이 기본값입니다. | 아니요 |
| `--base-url-secure` | 관리 및 상점 첫 화면에 다음 형식으로 액세스하는 데 사용할 보안 기본 URL: `http[s]://<host or ip>/<your install dir>/` | 아니요 |
| `--use-secure-admin` | `1` 는 SSL을 사용하여 관리자에 액세스함을 의미합니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0` 은 관리자가 SSL을 사용하지 않음을 의미합니다. 이것이 기본값입니다. | 아니요 |
| `--admin-use-security-key` | `1` 을 사용하면 애플리케이션이 임의로 생성된 키 값을 사용하여 관리자 및 양식의 페이지에 액세스합니다. 이러한 키 값은 크로스 사이트 스크립트 위조 공격을 방지하는 데 도움이 됩니다. 이것이 기본값입니다.<br/><br/>`0` 키 사용을 비활성화합니다. | 아니요 |
| `--magento-init-params` | 응용 프로그램 초기화 매개 변수를 사용자 지정하는 명령에 추가합니다.<br/><br/>예: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 아니요 |
