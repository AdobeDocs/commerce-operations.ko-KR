---
title: 설치 안내서
description: 이 안내서를 사용하여 설치 [!DNL Site-Wide Analysis Tool] 웹 사이트용
source-git-commit: 434fb9eb9570f183d9bf9d4b56b8e56a69e8005d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 설치 안내서

다음 [!DNL Site-Wide Analysis Tool] 에서는 24/7 클라우드 인프라 설치에서 Adobe Commerce의 보안 및 운영을 보장하기 위한 실시간 성능 모니터링, 보고서 및 권장 사항을 제공합니다. 또한 사용 가능하고 설치된 패치, 타사 확장 및 Adobe Commerce 설치에 대한 자세한 정보도 제공합니다.

>[!INFO]
>
>학습 [사용 방법](../site-wide-analysis-tool/access.md) a [!DNL Site-Wide Analysis Tool] 보고서를 생성합니다.

Adobe Commerce의 온-프레미스 설치가 있는 경우 도구를 사용하려면 인프라에 에이전트를 설치해야 합니다. 클라우드 인프라 프로젝트에서 Adobe Commerce에 에이전트를 설치할 필요가 없습니다.

## 에이전트

다음 [!DNL Site-Wide Analysis Tool] 에이전트를 사용하면 [!DNL Site-Wide Analysis Tool] Adobe Commerce의 온프레미스 설치에 대한 고객

다음 [!DNL Site-Wide Analysis Tool] 에이전트는 응용 프로그램 및 비즈니스 데이터를 수집하고 분석하여 설치 상태에 대한 추가 인사이트를 제공하므로 고객 경험을 향상시킬 수 있습니다. 애플리케이션을 모니터링하고 성능, 보안, 가용성 및 애플리케이션 문제를 식별하는 데 도움이 됩니다.

에이전트를 설치하려면 다음 단계가 필요합니다.

1. 시스템 요구 사항을 확인합니다.

1. 에서 API 키 구성 [!UICONTROL Commerce Services Connector] 확장.

1. 에이전트를 설치합니다.

1. 에이전트를 실행합니다.

>[!INFO]
>
>에이전트는 다중 노드 Adobe Commerce 설치를 지원합니다. 각 노드에 에이전트를 설치하고 구성해야 합니다.

## 시스템 요구 사항

에이전트를 설치하기 전에 온-프레미스 인프라가 다음 요구 사항을 충족해야 합니다.

- 운영 체제

   - [!DNL Linux x86-64] 배포와 같은 [!DNL RedHat Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], 및 유사
   >[!IMPORTANT]
   >
   >Adobe Commerce은 [!DNL Microsoft Windows] 또는 [!DNL macOS].

- Adobe Commerce 2.4.1 이상

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell 유틸리티

   - `grep`

   - `awk`

   - `nice`

   - `grep`

## [!DNL Commerce Services Connector]

에이전트에는 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 시스템 및 [구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) API 키 사용. 확장이 설치되어 있는지 확인하려면 다음 명령을 실행하십시오.

```bash
bin/magento module:status Magento_ServicesConnector
```

확장을 설치하고 다른 서비스에 대한 기존 API 키를 사용하여 구성한 경우, **API 키를 다시 생성해야 합니다.** 에이전트의 Adobe Commerce 관리에서 업데이트합니다.

1. 웹 사이트를 [유지 모드](../../installation/tutorials/maintenance-mode.md).

1. 에 로그인합니다. [accounts.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

1. 클릭 **[!UICONTROL API Portal]**.

1. 클릭 **[!UICONTROL Delete]** 기존 API 키 옆에 있습니다.

1. [구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 새 API 키.

>[!IMPORTANT]
>
> API 포털에서 새 키를 생성하는 경우 즉시 의 API 키를 업데이트합니다 [!DNL Admin configuration]. 새 키를 생성하고 [!DNL Admin]로 설정하면 SaaS 확장이 더 이상 작동하지 않으며 중요한 데이터를 잃게 됩니다.

확장이 설치되어 있지 않은 경우 다음 지침을 사용하여 설치합니다.

1. 확장을 `composer.json` 파일을 설치하고 설치합니다.

   ```bash
   composer require magento/services-connector:1.*
   ```

1. 확장을 활성화합니다.

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. 데이터베이스 스키마를 업데이트합니다.

   ```bash
   bin/magento setup:upgrade
   ```

1. [API 키 구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 확장을 시스템에 연결하기 위해

## 에이전트 설치

Adobe에서 [쉘 스크립트](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 설치를 단순화하는 데 도움이 됩니다. 셸 스크립트를 사용하는 것이 좋지만, [수동 설치](#manual) 필요한 경우 메서드를 사용합니다.

>[!INFO]
>
>에이전트가 설치되면 새 릴리스를 사용할 수 있으면 자체 업데이트됩니다.

### 스크립트 작성

1. 셸 스크립트를 다운로드하여 실행합니다.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >루트 Adobe Commerce 프로젝트 디렉토리 외부에 에이전트를 설치하는 것이 좋습니다.

1. 설치를 확인합니다.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 에이전트를 다운로드하여 설치한 후에는 다음을 수행해야 합니다 [실행할 구성](#run-the-agent) 다음 방법 중 하나를 사용합니다.

   - [서비스](#service) (루트 액세스 권한이 있는 경우 기본 설정)

   - [크론](#cron)

### 수동 {#manual}

Adobe의 [쉘 스크립트](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 에이전트를 설치하려면 다음 단계를 수행하여 수동으로 설치해야 합니다.

1. 에이전트를 다운로드할 디렉토리를 만듭니다.

   >[!TIP]
   >
   >루트 Adobe Commerce 프로젝트 디렉토리 외부에 에이전트를 설치하는 것이 좋습니다.

1. 이진 파일을 다운로드하여 압축을 해제합니다.

   >[!INFO]
   >
   >를 사용하려면 [!DNL Site-Wide Analysis Tool], 먼저 Adobe Commerce 관리자에서 대시보드에 액세스할 때 표시되는 사용 약관을 읽고 동의해야 합니다.

   대상 **AMD64** 아키텍처:

   1. 런처 아카이브를 다운로드합니다.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 런처 아카이브를 압축 해제합니다.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   대상 **ARM64** 아키텍처:

   1. 런처 아카이브를 다운로드합니다.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 런처 아카이브를 압축합니다.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```


1. *(선택 사항)* 체크섬 파일에 대한 서명을 확인합니다.

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

1. 만들기 `config.yaml` 다음 내용을 포함하는 파일입니다.

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

1. 에이전트를 다운로드하여 설치한 후에는 다음을 수행해야 합니다 [실행할 구성](#run-the-agent) 다음 방법 중 하나를 사용합니다.

   - [서비스](#service) (루트 액세스 권한이 있는 경우 기본 설정)

   - [크론](#cron)

## 에이전트 실행 {#run-the-agent}

서비스로 실행되도록 에이전트를 구성하는 것이 좋습니다. 인프라에 대한 액세스 권한이 제한되어 있고 루트 사용 권한이 없는 경우 [cron](#cron) 을 가리키도록 업데이트하는 것이 좋습니다.

### 서비스 {#service}

1. 시스템 단위 파일 만들기 `(/etc/systemd/system/scheduler.service)` 다음 구성으로 대체합니다(바꾸기 `<filesystemowner>` 에이전트 및 Adobe Commerce 소프트웨어가 설치된 디렉토리를 소유하는 Unix 사용자 사용) 에이전트를 루트 사용자로 다운로드한 경우 디렉토리 및 중첩 파일 소유자를 변경합니다.

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

1. 서비스가 작동 중인지 확인합니다.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### 크론 {#cron}

루트 권한이 없거나 서비스를 루트로 구성할 수 있는 권한이 없는 경우 대신 cron을 사용할 수 있습니다.

계획 일정을 업데이트합니다.

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## 제거

시스템에서 서비스를 제거하고 생성된 파일을 모두 제거하려면 다음 명령을 실행하십시오.

1. 스케줄러를 중지합니다.

   ```bash
   systemctl stop scheduler
   ```

1. 스케줄러를 비활성화합니다.

   ```bash
   systemctl disable scheduler
   ```

1. 스케줄러 서비스의 `systemd` 단위 파일입니다.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. 를 다시 로드합니다. `systemd` 관리자 구성.

   ```bash
   systemctl daemon-reload
   ```

1. 임의 재설정 `systemd` 실패 상태의 단위입니다.

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

에이전트를 대신 cron으로 실행하도록 구성한 경우 다음 지침을 사용하십시오.

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

## 구성 파일 무시

환경 변수를 사용하여 설치 중에 구성 파일에 지정한 값을 재정의할 수 있습니다. 이렇게 하면 이전 버전의 에이전트와의 이전 호환성을 유지합니다. 권장 값에 대해서는 다음 표를 참조하십시오.

| 속성 | 설명 |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | 에이전트를 설치할 때 제공한 회사 또는 사이트 이름 |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | PHP CLI 인터프리터에 대한 경로(일반적으로 `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | Adobe Commerce 애플리케이션이 설치된 루트 디렉토리(일반적으로 `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Adobe Commerce 설치용 데이터베이스 사용자 |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | Adobe Commerce 설치에 지정된 사용자의 데이터베이스 암호 |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Adobe Commerce 설치용 데이터베이스 호스트 |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Adobe Commerce 설치의 데이터베이스 이름 |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Adobe Commerce 설치에 대한 데이터베이스 포트(일반적으로 `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Adobe Commerce 설치 테이블 접두사(기본값: `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | Adobe Commerce 설치에 보조 데이터베이스 인스턴스가 있는지 여부(일반적으로 `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | 에이전트의 임시 디렉터리(일반적으로 `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | 첫 번째 실행 시 데이터 수집(일반적으로 `1`) |
| `SWAT_AGENT_LOG_LEVEL` | 심각도를 기준으로 기록되는 이벤트를 결정합니다(일반적으로 `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | 자동 업그레이드 활성화 (업그레이드 후 다시 시작해야 함) 에이전트가 옵션이 비활성화되어 있으면 업그레이드를 확인하지 않습니다. `true` 또는 `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | 스테이징 환경에서 에이전트를 사용하도록 샌드박스 모드 활성화 |

>[!INFO]
>
>자세한 내용은 [액세스 방법 [!DNL Site-Wide Analysis Tool] 보고서를 생성합니다](../site-wide-analysis-tool/access.md).
