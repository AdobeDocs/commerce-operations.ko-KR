---
title: 부트스트랩 매개 변수의 값 설정
description: Commerce 응용 프로그램에 대한 부트스트랩 매개 변수를 설정하는 방법을 알아봅니다.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# Bootstrap 매개 변수

이 항목에서는 Commerce 응용 프로그램 부트스트랩 매개 변수의 값을 설정하는 방법을 보여 줍니다. 자세한 내용은 [애플리케이션 초기화 및 부트스트래핑 개요](initialization.md).

다음 표에서는 설정할 수 있는 부트스트랩 매개 변수에 대해 설명합니다.

| Bootstrap 매개 변수 | 설명 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | 사용자 지정 디렉터리 및 URL 경로를 지정합니다 |
| MAGE_PROFILER | 종속성 그래프 및 HTML 프로파일링을 활성화합니다 |

>[!INFO]
>
>- 일부 부트스트랩 매개 변수는 문서화되지 않습니다.
>- 이제 다음을 사용하여 애플리케이션 모드(개발자, 기본, 프로덕션)를 설정합니다. [`magento deploy:mode:set {mode}`](../cli/set-mode.md) 명령.


## 환경 변수를 사용하여 매개 변수 설정

이 섹션에서는 환경 변수를 사용하여 부트스트랩 매개 변수의 값을 설정하는 방법을 설명합니다.

### 애플리케이션 모드 설정

부트스트랩 변수를 시스템 전체 환경 변수로 지정할 수 있으며, 이를 통해 모든 프로세스에서 이러한 변수를 사용할 수 있습니다.

예를 들어 `MAGE_PROFILER` 다음과 같이 모드를 지정하는 시스템 환경 변수:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

셸별 명령을 사용하여 변수를 설정합니다. 셸에 구문이 다르므로 다음 참조를 참조하십시오 [unix.stackexchange.com][unix-stackx].

CentOS에 대한 Bash 셸 예:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>다음과 같은 경우 `PHP Fatal error` 프로파일러 값을 설정한 후 브라우저에 표시하고 웹 서버를 다시 시작합니다. 그 이유는 바이트코드 및 PHP 클래스 경로를 캐시하는 PHP 바이트코드 캐싱과 관련될 수 있습니다.

## Apache 또는 Nginx에 대한 매개 변수 설정

이 섹션에서는 Apache 또는 Nginx에 대한 모드를 지정하는 방법에 대해 설명합니다.

### Nginx 설정

자세한 내용은 [Nginx 샘플 구성] on _GitHub_.

### Apache .htaccess 설정

애플리케이션 모드를 설정하는 한 가지 방법은 편집 `.htaccess`. 이렇게 하면 Apache 설정을 변경할 필요가 없습니다.

수정할 수 있습니다 `.htaccess` 전자 상거래 애플리케이션의 진입점에 따라 다음 위치 중 하나에서 다음을 수행합니다.

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**변수를 설정하려면 다음을 수행하십시오**:

1. 텍스트 편집기에서 이전 파일 중 하나를 열고 원하는 설정을 추가하거나 주석 처리를 취소합니다.

   예를 들어 [모드](application-modes.md)에서 다음 항목의 주석을 취소합니다.

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 값 설정 `MAGE_PROFILER` 다음 중 하나를 수행합니다.

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 변경 내용을 `.htaccess`; 변경 사항을 적용하려면 Apache를 다시 시작할 필요가 없습니다.

### Apache 설정

Apache 웹 서버는 `mod_env` 지시어

Apache `mod_env` 지시문은 [Apache 버전 2.2] 및 [Apache 버전 2.4].

다음 절차는 Apache 가상 호스트에서 애플리케이션 모드를 설정하는 방법을 보여 줍니다. 이 방법만이 `mod_env` 지시어 자세한 내용은 Apache 설명서를 참조하십시오.

>[!TIP]
>
>다음 섹션에서는 사용자가 이미 가상 호스트를 설정했다고 가정합니다. 없는 경우 다음과 같은 리소스를 참조하십시오. [이 DigitalOcean 자습서](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Ubuntu에서 Apache에 대한 부트스트랩 변수를 지정하려면**:

1. 을 사용하는 사용자 `root` 권한, 텍스트 편집기에서 가상 호스트 구성 파일을 엽니다.

   예를 들어, 가상 호스트의 이름이 인 경우 `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. 가상 호스트 구성의 아무 곳이나 다음 줄을 추가합니다.

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   For example,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 아직 활성화하지 않은 경우 가상 호스트를 활성화합니다.

   ```bash
   a2ensite <virtual host config file name>
   ```

   예,

   ```bash
   a2ensite my.magento.conf
   ```

1. 모드를 설정한 후 웹 서버를 다시 시작합니다.

   - 우분투: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>이 섹션에서는 사용자가 이미 가상 호스트를 설정했다고 가정합니다. 없는 경우 다음과 같은 리소스를 참조하십시오. [이 DigitalOcean 자습서](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**CentOS에서 Apache에 대한 부트스트랩 변수를 지정하려면**:

1. 을 사용하는 사용자 `root` 권한, 열기 `/etc/httpd/conf/httpd.conf` 텍스트 편집기에서 을 참조하십시오.

1. 가상 호스트 구성의 아무 곳이나 다음 줄을 추가합니다.

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   예,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.

1. 모드를 설정한 후 웹 서버를 다시 시작합니다.

   - 우분투: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache 버전 2.2]: http://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache 버전 2.4]: http://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx 샘플 구성]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
