---
title: 웹 서버 구성
description: Vannish에서 작동하도록 웹 서버를 구성하는 방법에 대해 알아봅니다.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# 웹 서버 구성

Varnish는 웹 서버가 아닌 들어오는 HTTP 요청에 직접 응답하므로 기본 포트 80 이외의 포트에서 수신하도록 웹 서버를 구성합니다.

다음 섹션에서는 포트 8080을 예로 사용합니다.

**Apache 2.4 수신 포트를 변경하려면**:

1. 텍스트 편집기에서 `/etc/httpd/conf/httpd.conf` 열기
1. `Listen` 지시문을 찾습니다.
1. 수신 포트의 값을 `8080`(으)로 변경합니다. 사용 가능한 수신 포트를 사용할 수 있습니다.
1. 변경 내용을 `httpd.conf`에 저장하고 텍스트 편집기를 종료합니다.

## 바니시 시스템 구성 수정

바니시 시스템 구성을 수정하려면

1. `root` 권한을 가진 사용자는 텍스트 편집기에서 Vanish 구성 파일을 엽니다.

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - 데비안: `/etc/default/varnish`
   - 우분투: `/etc/default/varnish`

1. Vannish 수신 포트를 80으로 설정합니다.

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Varnish 4.x의 경우 DAEMON_OPTS에 `-a` 매개 변수에 대한 올바른 수신 포트가 포함되어 있는지 확인합니다(VARNISH_LISTEN_PORT가 올바른 값으로 설정되어 있더라도).

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Varnish 구성 파일에 변경 사항을 저장하고 텍스트 편집기를 종료합니다.

### 기본 VCL 수정

이 섹션에서는 Varnish가 HTTP 응답 헤더를 반환하도록 최소 구성을 제공하는 방법에 대해 설명합니다. 이를 통해 Vannish를 사용하도록 [!DNL Commerce] 응용 프로그램을 구성하기 전에 Vannish가 작동하는지 확인할 수 있습니다.

바니시를 최소한으로 구성하려면

1. `default.vcl` 백업:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 텍스트 편집기에서 `/etc/varnish/default.vcl` 열기
1. 다음 별표를 찾습니다.

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. `.host`의 값을 Varnish _백엔드_ 또는 _원본 서버_&#x200B;의 정규화된 호스트 이름 또는 IP 주소 및 수신 대기 포트로 바꾸십시오. 즉, Varnish 콘텐츠를 제공하는 서버는 속도가 빨라집니다.

   일반적으로 웹 서버입니다. _바니시 가이드_&#x200B;에서 [백엔드 서버](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)를 참조하십시오.

1. `.port`의 값을 웹 서버의 수신 포트(이 예제에서는 8080)로 바꿉니다.

   예: Apache가 호스트 192.0.2.55에 설치되고 Apache가 포트 8080에서 수신 대기합니다.

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Adobe Varnish와 Apache가 동일한 호스트에서 실행 중인 경우 `localhost`이(가) 아닌 IP 주소 또는 호스트 이름을 사용하는 것이 좋습니다.

1. 변경 내용을 `default.vcl`에 저장하고 텍스트 편집기를 종료합니다.

1. 니시 다시 시작:

   ```bash
   service varnish restart
   ```

Vannish를 시작하지 못하면 다음과 같이 명령줄에서 실행해 보십시오.

```bash
varnishd -d -f /etc/varnish/default.vcl
```

오류 메시지가 표시됩니다.


>[!INFO]
>
>Vannish가 서비스로 시작되지 않는 경우 SELinux 규칙을 구성하여 실행할 수 있도록 해야 합니다.

## 바니시가 작동하는지 확인

다음 단원에서는 Vannish가 작동하지만 이를 사용하도록 Commerce을 구성하지 않고 _확인하는 방법에 대해 설명합니다._ Commerce을 구성하기 전에 이 작업을 시도해야 합니다.

다음 섹션에서 설명한 작업을 표시된 순서대로 수행합니다.

- [니스 시작](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### 니스 시작

입력: `service varnish start`

Vannish가 서비스로 시작되지 않으면 다음과 같이 명령줄에서 시작합니다.

1. Vannish CLI를 시작합니다.

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Vanish 하위 프로세스를 시작합니다.

   메시지가 표시되면 `start`을(를) 입력하십시오.

   성공적인 시작을 확인하기 위해 다음 메시지가 표시됩니다.

   ```
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

```
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

위의 예는 포트 80에서 실행되는 Varnish와 포트 8080에서 실행되는 Apache를 보여줍니다.

`varnishd`에 대한 출력이 표시되지 않으면 Vannish가 실행 중인지 확인하십시오.

[`netstat`개 옵션](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html)을 참조하세요.

## Commerce 소프트웨어 설치

아직 설치하지 않았다면 Commerce 소프트웨어를 설치합니다. 기본 URL을 입력하라는 메시지가 표시되면 Varnish는 모든 수신 HTTP 요청을 수신하므로 Varnish 호스트와 포트 80(Varnish용)을 사용합니다.

Commerce 설치 시 발생할 수 있는 오류:

```
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

이 오류가 발생하는 경우 `default.vcl`을(를) 편집하고 다음과 같이 `backend` 스타자에 시간 제한을 추가하십시오.

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## HTTP 응답 헤더 확인

이제 모든 페이지에서 반환된 HTML 응답 헤더를 확인하여 Varnish가 페이지를 제공하는지 확인할 수 있습니다.

헤더를 보려면 먼저 Commerce을 개발자 모드로 설정해야 합니다. 몇 가지 방법이 있습니다. 그 중 가장 간단한 방법은 Commerce 응용 프로그램 루트에서 `.htaccess`을(를) 수정하는 것입니다. [`magento deploy:mode:set`](../cli/set-mode.md) 명령을 사용할 수도 있습니다.

### 개발자 모드용 Commerce 설정

Commerce을 개발자 모드로 설정하려면 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) 명령을 사용합니다.

### Varnish 로그 보기

Varnish가 실행 중인지 확인한 다음 Varnish 서버에 다음 명령을 입력합니다.

```bash
varnishlog
```

웹 브라우저에서 임의의 Commerce 페이지로 이동합니다.

명령 프롬프트 창에 긴 응답 헤더 목록이 표시됩니다. 다음과 같은 헤더를 찾습니다.

```
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

이러한 헤더가 _표시되지 않음_&#x200B;인 경우 바니시를 중지하고 `default.vcl`을(를) 확인한 다음 다시 시도하십시오.

### HTML 응답 헤더 확인

응답 헤더를 확인하는 방법에는 브라우저 플러그인 또는 브라우저 관리자 사용을 비롯한 여러 가지가 있습니다.

다음 예제에서는 `curl`을(를) 사용합니다. HTTP를 사용하여 Commerce 서버에 액세스할 수 있는 모든 컴퓨터에서 이 명령을 입력할 수 있습니다.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

For example,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

다음과 같은 헤더를 찾습니다.

```
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
