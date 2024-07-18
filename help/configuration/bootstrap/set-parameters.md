---
title: 부트스트랩 매개 변수 값 설정
description: Commerce 애플리케이션에 대한 부트스트랩 매개 변수를 설정하는 방법에 대해 알아봅니다.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Bootstrap 매개 변수

이 항목에서는 Commerce 애플리케이션 부트스트랩 매개 변수의 값을 설정하는 방법을 보여줍니다. [응용 프로그램 초기화 및 부트스트래핑 개요](initialization.md)를 참조하십시오.

다음 표에서는 설정할 수 있는 부트스트랩 매개 변수에 대해 설명합니다.

| Bootstrap 매개 변수 | 설명 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | 사용자 지정 디렉터리 및 URL 경로 지정 |
| MAGE_PROFILER | 종속성 그래프 및 HTML 프로파일링 활성화 |

>[!INFO]
>
>- 일부 부트스트랩 매개 변수가 문서화되어 있지는 않습니다.
>- 이제 [`magento deploy:mode:set {mode}`](../cli/set-mode.md) 명령을 사용하여 응용 프로그램 모드(개발자, 기본값, 프로덕션)를 설정합니다.

## 환경 변수를 사용하여 매개 변수 설정

이 섹션에서는 환경 변수를 사용하여 부트스트랩 매개 변수의 값을 설정하는 방법에 대해 설명합니다.

### 애플리케이션 모드 설정

부트스트랩 변수를 모든 프로세스에서 사용할 수 있도록 하는 시스템 전체 환경 변수로 지정할 수 있습니다.

예를 들어 `MAGE_PROFILER` 시스템 환경 변수를 사용하여 다음과 같이 모드를 지정할 수 있습니다.

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

셸별 명령을 사용하여 변수를 설정합니다. 셸의 구문이 다르므로 [unix.stackexchange.com][unix-stackx]과(와) 같은 참조를 참조하십시오.

CentOS에 대한 Bash 셸 예:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>프로파일러 값을 설정한 후 브라우저에 `PHP Fatal error`이(가) 표시되면 웹 서버를 다시 시작합니다. 그 이유는 PHP 바이트코드 캐싱과 관련이 있을 수 있는데, 이것은 바이트코드와 PHP 클래스 공간을 캐싱한다.

## Apache 또는 Ngix에 대한 매개 변수 설정

이 섹션에서는 Apache 또는 Nginx에 대한 모드를 지정하는 방법에 대해 설명합니다.

### Nginx 설정

_GitHub_&#x200B;에서 [Nginx 샘플 구성]을 참조하세요.

### Apache .htaccess 설정

응용 프로그램 모드를 설정하는 한 가지 방법은 `.htaccess`을(를) 편집하는 것입니다. 이렇게 하면 Apache 설정을 변경할 필요가 없습니다.

Commerce 응용 프로그램의 시작 지점에 따라 다음 위치에서 `.htaccess`을(를) 수정할 수 있습니다.

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**변수를 설정하려면**:

1. 텍스트 편집기에서 이전 파일을 열고 원하는 설정을 추가하거나 주석 처리를 제거합니다.

   예를 들어 [mode](application-modes.md)을(를) 지정하려면 다음 주석을 제거하십시오.

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. `MAGE_PROFILER`의 값을 다음 중 하나로 설정하십시오.

   ```
   firebug
   csvfile
   <custom value>
   ```

1. 변경 내용을 `.htaccess`에 저장하십시오. 변경 내용을 적용하려면 Apache를 다시 시작할 필요가 없습니다.

### Apache 설정

Apache 웹 서버는 `mod_env` 지시문을 사용하여 응용 프로그램 모드 설정을 지원합니다.

Apache `mod_env` 지시문이 [Apache 버전 2.2]과(와) [Apache 버전 2.4]에서 약간 다릅니다.

다음 절차는 Apache 가상 호스트에서 애플리케이션 모드를 설정하는 방법을 보여 줍니다. 이것이 `mod_env` 지시문을 사용하는 유일한 방법은 아닙니다. 자세한 내용은 Apache 설명서를 참조하십시오.

>[!TIP]
>
>다음 섹션에서는 가상 호스트를 이미 설정했다고 가정합니다. 아직 없으면 [이 DigitalOcean 자습서](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)와 같은 리소스를 참조하십시오.

**Ubuntu에서 Apache에 대한 부트스트랩 변수를 지정하려면**:

1. `root` 권한이 있는 사용자는 텍스트 편집기에서 가상 호스트 구성 파일을 여십시오.

   예를 들어 가상 호스트의 이름이 `my.magento`인 경우

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. 가상 호스트 구성의 모든 위치에서 다음 줄을 추가합니다.

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   For example,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 가상 호스트를 활성화하지 않은 경우 다음을 수행합니다.

   ```bash
   a2ensite <virtual host config file name>
   ```

   For example,

   ```bash
   a2ensite my.magento.conf
   ```

1. 모드를 설정한 후 웹 서버를 다시 시작합니다.

   - 우분투: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>이 섹션에서는 가상 호스트를 이미 설정했다고 가정합니다. 아직 없으면 [이 DigitalOcean 자습서](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6)와 같은 리소스를 참조하십시오.

**CentOS에서 Apache에 대한 부트스트랩 변수를 지정하려면**:

1. `root` 권한이 있는 사용자는 텍스트 편집기에서 `/etc/httpd/conf/httpd.conf`을(를) 엽니다.

1. 가상 호스트 구성의 모든 위치에서 다음 줄을 추가합니다.

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   For example,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.

1. 모드를 설정한 후 웹 서버를 다시 시작합니다.

   - 우분투: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache 버전 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache 버전 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx 샘플 구성]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
