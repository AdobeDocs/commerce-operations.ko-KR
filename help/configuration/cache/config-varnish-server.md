---
title: 웹 서버 구성
description: Varnish에서 작동하도록 웹 서버를 구성하는 방법을 알아봅니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# 웹 서버 구성

웹 서버가 아닌 들어오는 HTTP 요청에 Varnish가 직접 응답하므로 기본 포트 80 이외의 포트에서 수신 대기하도록 웹 서버를 구성합니다.

다음 섹션에서는 포트 8080을 예로 사용합니다.

**Apache 2.4 수신 포트를 변경하려면**:

1. 열기 `/etc/httpd/conf/httpd.conf` 텍스트 편집기에서 을 참조하십시오.
1. 을(를) 찾습니다 `Listen` 지시문
1. 수신 포트 값을 다음으로 변경합니다. `8080`. 사용 가능한 수신 포트를 사용할 수 있습니다.
1. 변경 내용을 `httpd.conf` 텍스트 편집기를 종료합니다.

## Varnish 시스템 구성 수정

Varnish 시스템 구성을 수정하려면 다음을 수행합니다.

1. 을 사용하는 사용자 `root` privileges, 텍스트 편집기에서 제거 구성 파일을 엽니다.

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - 우분투: `/etc/default/varnish`

1. Varnish 수신 포트를 80으로 설정합니다.

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Varnish 4.x의 경우 DAEMON_OPTS에 `-a` 매개변수(VARNISH_LISTEN_PORT가 올바른 값으로 설정된 경우에도):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 변경 사항을 Varnish 구성 파일에 저장하고 텍스트 편집기를 종료합니다.

### 기본 VCL 수정

이 섹션에서는 Varnish가 HTTP 응답 헤더를 반환하도록 최소 구성을 제공하는 방법에 대해 설명합니다. 이렇게 하면 을 구성하기 전에 Varnish가 작동하는지 확인할 수 있습니다 [!DNL Commerce] Varnish를 사용할 응용 프로그램입니다.

Varnish를 최소 구성하려면

1. 백업 `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 열기 `/etc/varnish/default.vcl` 텍스트 편집기에서 을 참조하십시오.
1. 다음 상태를 찾습니다.

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 값 바꾸기 `.host` 정규화된 호스트 이름 또는 Varnish의 IP 주소 및 수신 포트 사용 _백엔드_ 또는 _원본 서버_; 즉, Varnish라는 컨텐츠를 제공하는 서버는 가속화될 것입니다.

   일반적으로 웹 서버입니다. 자세한 내용은 [백엔드 서버](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) 에서 _Varnish 안내서_.

1. 값 바꾸기 `.port` 웹 서버의 수신 대기 포트(이 예제의 경우 8080) 사용

   예: Apache는 호스트 192.0.2.55에 설치되며 Apache는 포트 8080에서 수신 대기합니다.

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Varnish와 Apache가 동일한 호스트에서 실행 중인 경우 Adobe은 IP 주소 또는 호스트 이름을 사용하지 않고 사용할 것을 권장합니다 `localhost`.

1. 변경 내용을 `default.vcl` 텍스트 편집기를 종료합니다.

1. Varnish를 다시 시작합니다.

   ```bash
   service varnish restart
   ```

Varnish를 시작하지 못하면 다음과 같이 명령줄에서 실행해 보십시오.

```bash
varnishd -d -f /etc/varnish/default.vcl
```

오류 메시지가 표시됩니다.


>[!INFO]
>
>Varnish가 서비스로 시작되지 않는 경우 SELinux 규칙을 실행하여 실행해야 합니다.

## Varnish가 작동하는지 확인

다음 섹션에서는 Varnish가 작동하는지 확인할 수 있는 방법에 대해 설명합니다. _사용 안 함_ 사용하도록 상거래 구성. 상거래를 구성하기 전에 이를 시도해야 합니다.

다음 섹션에서 설명한 작업을 표시된 순서대로 수행합니다.

- [바니쉬 시작](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### 바니쉬 시작

다음을 입력합니다. `service varnish start`

Varnish가 서비스로 시작하지 않으면 다음과 같이 명령줄에서 시작합니다.

1. Varnish CLI 시작:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Varnish 하위 프로세스를 시작합니다.

   메시지가 표시되면 을 입력합니다. `start`

   다음 메시지가 표시되어 성공적인 시작을 확인합니다.

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Varnish 서버에 로그인하고 다음 명령을 입력합니다.

```bash
netstat -tulpn
```

특히 다음 출력을 찾습니다.

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

앞의 내용은 포트 80에서 실행되는 Varnish와 포트 8080에서 실행되는 Apache를 보여줍니다.

에 대한 출력이 표시되지 않으면 `varnishd`Varnish가 실행되고 있는지 확인합니다.

자세한 내용은 [`netstat` 옵션](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## 상거래 소프트웨어 설치

아직 설치하지 않았다면 상거래 소프트웨어를 설치합니다. 기본 URL을 입력하라는 메시지가 표시되면 Varnish가 들어오는 모든 HTTP 요청을 수신하므로 Varnish 호스트와 포트 80(Varnish의 경우)을 사용합니다.

상거래 설치 오류:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

이 오류가 발생하는 경우 다음을 편집합니다. `default.vcl` 시간 초과를 `backend` stanza는 다음과 같습니다.

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## HTTP 응답 헤더 확인

이제 모든 페이지에서 반환된 HTML 응답 헤더를 확인하여 Varnish가 페이지를 제공하는지 확인할 수 있습니다.

헤더를 보려면 먼저 개발자 모드에 대해 상거래를 설정해야 합니다. 여러 가지 방법을 사용할 수 있으며 가장 간단한 방법은 를 수정하는 것입니다 `.htaccess` ( Commerce Application root)를 참조하십시오. 를 사용할 수도 있습니다 [`magento deploy:mode:set`](../cli/set-mode.md) 명령.

### 개발자 모드에 대한 상거래 설정

개발자 모드에 대해 상거래를 설정하려면 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) 명령.

### Varnish 로그 보기

Varnish가 실행 중인지 확인한 다음 Varnish 서버에 다음 명령을 입력합니다.

```bash
varnishlog
```

웹 브라우저에서 임의의 상거래 페이지로 이동합니다.

명령 프롬프트 창에 긴 응답 헤더 목록이 표시됩니다. 다음과 같은 헤더를 찾습니다.

```terminal
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

다음과 같은 헤더가 _not_ 표시, 변명 중지, `default.vcl`, 다시 시도하십시오.

### HTML 응답 헤더 보기

브라우저 플러그인 또는 브라우저 관리자 사용을 포함하여 응답 헤더를 확인하는 방법에는 여러 가지가 있습니다.

다음 예제에서는 를 사용합니다 `curl`. HTTP를 사용하여 상거래 서버에 액세스할 수 있는 모든 컴퓨터에서 이 명령을 입력할 수 있습니다.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

예,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

다음과 같은 헤더를 찾습니다.

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
