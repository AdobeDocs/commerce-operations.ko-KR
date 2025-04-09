---
title: 설치 안내서
description: 웹 사이트에  [!DNL Site-Wide Analysis Tool] 을(를) 설치하려면 이 안내서를 사용하십시오.
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# 설치 안내서

>[!IMPORTANT]
>
>2024년 4월 23일부터 모든 Adobe Commerce 온-프레미스 고객에 대한 [!DNL Site-Wide Analysis Tool]의 서비스가 중단됩니다.

[!DNL Site-Wide Analysis Tool]은(는) 클라우드 인프라 설치에서 Adobe Commerce의 보안 및 운영을 보장하기 위해 연중무휴 실시간 성능 모니터링, 보고서 및 권장 사항을 제공합니다. 또한 사용 가능하고 설치된 패치, 타사 확장 및 Adobe Commerce 설치에 대한 자세한 정보를 제공합니다.

>[!INFO]
>
>[!DNL Site-Wide Analysis Tool]을(를) [활성화](../site-wide-analysis-tool/access.md)하고 보고서를 생성하는 방법에 대해 알아봅니다.

Adobe Commerce을 온-프레미스에 설치한 경우 인프라에 에이전트를 설치하여 도구를 사용합니다. 클라우드 인프라 프로젝트의 Adobe Commerce에 에이전트를 설치할 필요가 없습니다.

## 에이전트

[!DNL Site-Wide Analysis Tool] 에이전트를 사용하면 Adobe Commerce의 온-프레미스 설치에 [!DNL Site-Wide Analysis Tool]을(를) 사용할 수 있습니다.

[!DNL Site-Wide Analysis Tool] 에이전트는 응용 프로그램 및 비즈니스 데이터를 수집하고 분석하여 고객 경험을 개선할 수 있도록 설치 상태에 대한 추가적인 통찰력을 제공합니다. 애플리케이션을 모니터링하고 성능, 보안, 가용성 및 애플리케이션 문제를 식별하는 데 도움이 됩니다.

에이전트를 설치하려면 다음 단계가 필요합니다.

1. 시스템 요구 사항을 확인합니다.

1. [!UICONTROL Commerce Services Connector] 확장에서 API 키를 구성합니다.

1. 에이전트를 설치합니다.

1. 에이전트를 실행합니다.

>[!INFO]
>
>에이전트는 다중 노드 Adobe Commerce 설치를 지원합니다. 각 노드에 에이전트를 설치하고 구성합니다.

## 시스템 요구 사항

에이전트를 설치하기 전에 온-프레미스 인프라가 다음 요구 사항을 충족해야 합니다.

- 운영 체제

   - [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian] 등 [!DNL Linux x86-64] 배포

  >[!IMPORTANT]
  >
  >Adobe Commerce은 [!DNL Microsoft Windows] 또는 [!DNL macOS]에서 지원되지 않습니다.

- Adobe Commerce 2.4.5-p1 이상(서비스 커넥터의 종속성으로 인해)

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell 유틸리티

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

에이전트를 사용하려면 시스템에 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) 확장을 설치하고 API 키를 사용하여 [구성](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html)해야 합니다. 확장이 설치되어 있는지 확인하려면 다음 명령을 실행합니다.

```bash
bin/magento module:status Magento_ServicesId
```

확장을 설치하고 다른 서비스에 대한 기존 API 키를 사용하여 구성한 경우 **API 키를 다시 생성하고** 에이전트의 Adobe Commerce 관리에서 업데이트해야 합니다.

1. 웹 사이트를 [유지 관리 모드](../../installation/tutorials/maintenance-mode.md)로 전환합니다.

1. [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671)에 로그인합니다.

   >[!NOTE]
   >
   > 계정에 액세스하는 데 문제가 있는 경우 문제 해결 도움말은 [Adobe Commerce 지원 또는 클라우드 계정에 로그인할 수 없음](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)을 참조하세요.

1. **[!UICONTROL API Portal]**&#x200B;을(를) 클릭합니다.

1. 기존 API 키 옆에 있는 **[!UICONTROL Delete]**&#x200B;을(를) 클릭합니다.

1. 새 API 키를 [구성](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html)합니다.

>[!IMPORTANT]
>
> API 포털에서 새 키를 생성하는 경우 [!DNL Admin configuration]에서 API 키를 즉시 업데이트합니다. 새 키를 생성하고 [!DNL Admin]의 키를 업데이트하지 않으면 SaaS 확장이 더 이상 작동하지 않으며 중요한 데이터를 잃게 됩니다.

확장이 설치되지 않은 경우 다음 지침에 따라 설치하십시오.

1. 확장을 `composer.json` 파일에 추가하고 설치하십시오.

   ```bash
   composer require magento/services-id
   ```

1. 확장을 활성화합니다.

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. 데이터베이스 스키마를 업데이트합니다.

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시를 지웁니다.

   ```bash
   bin/magento cache:clean
   ```

1. 확장을 시스템에 연결하려면 [API 키를 구성](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html)하십시오.

## 에이전트 설치

설치를 단순화하기 위해 [셸 스크립트](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh)를 만들었습니다. 셸 스크립트를 사용하는 것이 좋지만 필요한 경우 [수동 설치](#manual) 메서드를 따를 수 있습니다.

>[!INFO]
>
>에이전트가 설치되면 새 릴리스를 사용할 수 있을 때 자동으로 업데이트됩니다.

### 스크립팅됨

1. 셸 스크립트를 다운로드하고 실행합니다.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >에이전트를 루트 Adobe Commerce 프로젝트 디렉터리 외부에 설치하는 것이 좋습니다.

1. 설치를 확인합니다.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 에이전트를 다운로드하고 설치한 후 다음 방법 중 하나를 사용하여 [실행되도록 구성](#run-the-agent)합니다.

   - [서비스](#service)(루트 액세스 권한이 있는 경우 기본 설정)

   - [크론](#cron)

### 수동 {#manual}

[셸 스크립트](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh)를 사용하여 에이전트를 설치하지 않으려면 다음 단계에 따라 수동으로 설치해야 합니다.

1. 에이전트를 다운로드할 디렉토리를 만듭니다.

   >[!TIP]
   >
   >에이전트를 루트 Adobe Commerce 프로젝트 디렉터리 외부에 설치하는 것이 좋습니다.

1. 이진 파일을 다운로드하고 압축을 풉니다.

   >[!INFO]
   >
   >[!DNL Site-Wide Analysis Tool]을(를) 사용하려면 먼저 Adobe Commerce 관리자로부터 대시보드에 액세스할 때 표시되는 사용 약관을 읽고 동의해야 합니다.

   **AMD64** 아키텍처의 경우

   1. 런처 아카이브를 다운로드합니다.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 런처 아카이브 압축을 풉니다.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   **ARM64** 아키텍처의 경우

   1. 런처 아카이브를 다운로드합니다.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 런처 아카이브 압축을 풉니다.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(선택 사항)* 체크섬 파일에 대한 서명을 확인하십시오.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(선택 사항)* 체크섬을 확인합니다.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. 다음 내용으로 `config.yaml` 파일을 만듭니다.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. 설치를 확인합니다.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 에이전트를 다운로드하여 설치한 후에는 다음 방법 중 하나를 사용하여 [실행되도록 구성](#run-the-agent)해야 합니다.

   - [서비스](#service)(루트 액세스 권한이 있는 경우 기본 설정)

   - [크론](#cron)

## 에이전트 실행 {#run-the-agent}

서비스로 실행되도록 에이전트를 구성하는 것이 좋습니다. 인프라에 대한 액세스가 제한되어 있고 루트 권한이 없는 경우 대신 [cron](#cron)을 사용해야 합니다.

### 서비스 {#service}

1. 다음 구성으로 시스템 단위 파일 `(/etc/systemd/system/scheduler.service)`을(를) 만듭니다. `<filesystemowner>`을(를) 에이전트와 Adobe Commerce 소프트웨어가 설치된 디렉터리를 소유하는 UNIX® 사용자로 바꿉니다. 에이전트를 루트 사용자로 다운로드한 경우 디렉터리 및 중첩된 파일 소유자를 변경합니다.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. 서비스를 시작합니다.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. 서비스가 작동 및 실행 중인지 확인합니다.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### 크론 {#cron}

루트 권한이 없거나 서비스를 루트로 구성할 수 있는 권한이 없는 경우 cron 을 대신 사용할 수 있습니다.

cron 일정 업데이트:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## 제거

다음 명령을 실행하여 시스템에서 서비스를 제거하고 생성된 모든 파일을 제거합니다.

1. 스케줄러를 중지합니다.

   ```bash
   systemctl stop scheduler
   ```

1. 스케줄러를 비활성화합니다.

   ```bash
   systemctl disable scheduler
   ```

1. 스케줄러 서비스의 `systemd` 단위 파일을 제거합니다.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. `systemd` 관리자 구성을 다시 로드합니다.

   ```bash
   systemctl daemon-reload
   ```

1. 실패 상태에서 `systemd`단위를 다시 설정합니다.

   ```bash
   systemctl reset-failed
   ```

1. 스케줄러 서비스 디렉터리를 제거합니다.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. 스케줄러 이진 파일을 제거합니다.

   ```bash
   rm /usr/local/bin/scheduler
   ```

대신 cron을 사용하여 실행되도록 에이전트를 구성한 경우 다음 지침을 따르십시오.

1. crontab 목록에서 에이전트를 제거합니다.

   ```bash
   crontab -e
   ```

1. 실행 중인 작업을 중지합니다.

   ```bash
   ps aux | grep scheduler
   ```

1. 에이전트를 설치한 디렉토리를 제거합니다.

   ```bash
   rm -rf swat-agent
   ```

## 문제 해결

### 액세스 키가 제대로 구문 분석되지 않음

액세스 키가 제대로 구문 분석되지 않으면 다음 오류가 표시될 수 있습니다.

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

이 오류를 해결하려면 다음 단계를 수행하십시오.

1. [스크립팅된 설치](#scripted)를 수행하고, 출력을 저장하고, 출력에 오류가 있는지 검토하십시오.
1. 생성된 `config.yaml` 파일을 검토하고 Commerce 인스턴스와 PHP에 대한 경로가 올바른지 확인하십시오.
1. 스케줄러를 실행하는 사용자가 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md) Unix 그룹에 있거나 파일 시스템 소유자와 동일한 사용자인지 확인하십시오.
1. [Commerce 서비스 커넥터](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) 키가 올바르게 설치되어 있는지 확인하고 업데이트를 통해 확장을 시스템에 연결하십시오.
1. 키를 업데이트하고 [설치 스크립트](#scripted)를 사용하여 다시 설치한 후 에이전트를 [제거](#uninstall)합니다.
1. 스케줄러를 실행하여 동일한 오류가 계속 표시되는지 확인합니다.
1. 동일한 오류가 계속 발생하면 `config.yaml`에서 로그 수준을 높여 디버깅하고 지원 티켓을 엽니다.

### *SIGFAULT* 오류

바이너리를 실행할 때 *SIGFAULT* 오류가 표시되면 Adobe Commerce 및 에이전트 파일의 파일 소유자로 실행하지 않을 수 있습니다.
해결하려면 에이전트 디렉터리에 있는 모든 파일 중 Adobe Commerce 파일이 가진 파일 소유자와 동일한 사용자가 있고 바이너리가 해당 사용자에서도 실행되어야 하는지 확인하십시오.
`chown` 명령을 사용하여 파일 소유자를 변경하고 적절한 사용자로 전환할 수 있습니다.
데몬화 메커니즘(Cron 또는 System.d)이 적절한 사용자 아래에서 프로세스를 실행하는지 확인합니다.

>[!INFO]
>
>[액세스 방법 [!DNL Site-Wide Analysis Tool] 보고서 생성 방법](../site-wide-analysis-tool/access.md)을 참조하세요.
