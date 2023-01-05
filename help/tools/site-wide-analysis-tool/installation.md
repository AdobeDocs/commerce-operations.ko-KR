---
title: 설치 안내서
description: "이 안내서를 사용하여 설치 [!DNL Site-Wide Analysis Tool] 웹 사이트용"
source-git-commit: 0c27d4cf5854161e14a482912941cd144ca654f7
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# 설치 안내서

다음 [!DNL Site-Wide Analysis Tool] 에서는 24/7 클라우드 인프라 설치에서 Adobe Commerce의 보안 및 운영을 보장하기 위한 실시간 성능 모니터링, 보고서 및 권장 사항을 제공합니다. 또한 사용 가능하고 설치된 패치, 타사 확장 및 Adobe Commerce 설치에 대한 자세한 정보도 제공합니다.

>[!INFO]
>
>학습 [사용 방법](../site-wide-analysis-tool/access.md) a [!DNL Site-Wide Analysis Tool] 보고서를 생성합니다.

Adobe Commerce에 대한 온-프레미스 설치가 있는 경우 도구를 사용하려면 인프라에 에이전트를 설치하십시오. 클라우드 인프라 프로젝트에서 Adobe Commerce에 에이전트를 설치할 필요가 없습니다.

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
>에이전트는 다중 노드 Adobe Commerce 설치를 지원합니다. 각 노드에 에이전트를 설치하고 구성합니다.

## 시스템 요구 사항

에이전트를 설치하기 전에 온-프레미스 인프라가 다음 요구 사항을 충족해야 합니다.

- 운영 체제

   - [!DNL Linux x86-64] 배포와 같은 [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], 및 유사
   >[!IMPORTANT]
   >
   >Adobe Commerce은 [!DNL Microsoft Windows] 또는 [!DNL macOS].

- Adobe Commerce 2.4.1 이상

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

에이전트에는 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 시스템 및 [구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) API 키 사용. 확장이 설치되어 있는지 확인하려면 다음 명령을 실행하십시오.

```bash
bin/magento module:status Magento_ServicesId
```

확장을 설치하고 다른 서비스에 대한 기존 API 키를 사용하여 구성한 경우, **API 키를 다시 생성해야 합니다.** 에이전트의 Adobe Commerce 관리에서 업데이트합니다.

1. 웹 사이트를 [유지 모드](../../installation/tutorials/maintenance-mode.md).

1. 에 로그인합니다. [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > 계정에 액세스하는 데 문제가 있으면 [Adobe Commerce 지원 또는 클라우드 계정에 로그인할 수 없습니다.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) 문제 해결 도움말 을 참조하십시오.

1. 클릭 **[!UICONTROL API Portal]**.

1. 클릭 **[!UICONTROL Delete]** 기존 API 키 옆에 있습니다.

1. [구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 새 API 키.

>[!IMPORTANT]
>
> API 포털에서 새 키를 생성하는 경우 즉시 의 API 키를 업데이트합니다 [!DNL Admin configuration]. 새 키를 생성하고 [!DNL Admin]로 설정하면 SaaS 확장이 더 이상 작동하지 않으며 중요한 데이터를 잃게 됩니다.

확장이 설치되어 있지 않은 경우 다음 지침을 사용하여 설치합니다.

1. 확장을 `composer.json` 파일을 설치하고 설치합니다.

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

1. 에이전트를 다운로드하여 설치한 후 [실행할 구성](#run-the-agent) 다음 방법 중 하나를 사용합니다.

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

   1. 런처 아카이브를 압축 해제합니다.

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

1. 시스템 단위 파일 만들기 `(/etc/systemd/system/scheduler.service)` 다음 구성으로 대체합니다(바꾸기 `<filesystemowner>` 에이전트 및 Adobe Commerce 소프트웨어가 설치된 디렉토리를 소유하는 UNIX® 사용자 사용) 에이전트를 루트 사용자로 다운로드한 경우 디렉토리 및 중첩 파일 소유자를 변경합니다.

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

## 문제 해결

### 액세스 키가 제대로 구문 분석되지 않았습니다.

액세스 키를 제대로 구문 분석하지 않으면 다음 오류가 표시될 수 있습니다.

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.swat.magento.com/linux-amd64.json: 403 Forbidden
```

이 오류를 해결하려면 다음 단계를 수행하십시오.

1. 작업 [스크립트 설치](#scripted)를 눌러 출력을 저장하고 출력에 오류를 검토합니다.
1. 생성된 를 검토합니다 `config.yaml` 파일을 작성하고 Commerce 인스턴스와 PHP의 경로가 올바른지 확인합니다.
1. 스케줄러를 실행 중인 사용자가 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md) Unix 그룹 또는 는 파일 시스템 소유자와 동일한 사용자입니다.
1. 다음을 확인합니다. [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 키가 올바르게 설치되어 있고 해당 키를 업데이트하여 확장을 시스템에 연결해 보십시오.
1. [제거](#uninstall) 키를 업데이트한 후 에이전트를 사용하여 다시 설치합니다. [스크립트 설치](#scripted).
1. 스케줄러를 실행하고 동일한 오류가 계속 표시되는지 확인합니다.
1. 여전히 동일한 오류가 표시되면 `config.yaml` 지원 티켓을 디버깅하여 엽니다.


>[!INFO]
>
>자세한 내용은 [액세스 방법 [!DNL Site-Wide Analysis Tool] 보고서를 생성합니다](../site-wide-analysis-tool/access.md).
