---
title: 바니시 캐싱을 위한 nginx 구성
description: Adobe Commerce에 대한 바니시 캐싱과 작동하도록 웹 서버를 구성하는 방법을 알아봅니다. 포트 구성 및 설정 요구 사항을 살펴봅니다.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# 바니시 캐싱에 대한 nginx 구성 {#configure-web-server-for-varnish-caching}

Varnish가 Adobe Commerce 앞의 전체 페이지 캐시로 사용되는 경우 Varnish는 일반적으로 공개 HTTP 포트에서 수신하고 8080과 같이 기본이 아닌 백엔드 포트의 nginx에 요청을 전달합니다. Commerce 오리진 서버에 대한 nginx 사이트 구성을 업데이트하여 Varnish가 사용할 백엔드 포트에서 수신합니다.

{{varnish-config-cloud}}

다음 섹션에서는 포트 8080을 예로 사용합니다.

**Commerce 원본 서버의 nginx 수신 포트를 변경합니다**:

1. 텍스트 편집기에서 Adobe Commerce 원본 서버에 대한 nginx 사이트 구성을 엽니다.

위치는 운영 체제와 nginx 레이아웃에 따라 다릅니다. 예를 들어 Ubuntu는 `/etc/nginx/sites-available/` 아래의 파일을 사용하는 경우가 많습니다.

1. Commerce 사이트의 `server` 블록에서 공용 HTTP 포트에서 `listen` 지시문을 Varnish가 nginx에 연결하는 데 사용할 백엔드 포트로 변경합니다.

   예: 변경

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   끝:

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. 파일을 저장합니다.

1. nginx 구성을 확인합니다.

   ```shell
   nginx -t
   ```

1. nginx 다시 시작:

   ```shell
   systemctl restart nginx
   ```

## 바니시 시스템 구성 수정

백엔드 포트에서 수신하도록 nginx를 업데이트한 후 요청을 해당 호스트 및 포트로 전달하도록 Varnish를 구성합니다. For example:

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### 기본 VCL 수정

이 섹션에서는 Varnish가 HTTP 응답 헤더를 반환하도록 최소 구성을 제공하는 방법에 대해 설명합니다. 이를 통해 Vannish를 사용하도록 [!DNL Commerce] 응용 프로그램을 구성하기 전에 Vannish가 작동하는지 확인할 수 있습니다.

바니시를 최소한으로 구성하려면

1. `default.vcl` 백업:

   ```shell
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

   예: nginx가 192.0.2.55 호스트에 설치되어 있고 포트 8080에서 수신 대기 중:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Varnish와 nginx가 동일한 호스트에서 실행 중인 경우 Adobe은 `localhost`이(가) 아닌 IP 주소 또는 호스트 이름을 사용할 것을 권장합니다.

1. 변경 내용을 `default.vcl`에 저장하고 텍스트 편집기를 종료합니다.

1. 니시 다시 시작:

   ```shell
   service varnish restart
   ```

Vannish를 시작하지 못하면 다음과 같이 명령줄에서 실행해 보십시오.

```shell
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
- [`netstat`](#netstat)

### 니스 시작

입력: `service varnish start`

Vannish가 서비스로 시작되지 않으면 다음과 같이 명령줄에서 시작합니다.

1. Vannish CLI를 시작합니다.

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Vanish 하위 프로세스를 시작합니다.

   메시지가 표시되면 `start`을(를) 입력하십시오.

   성공적인 시작을 확인하기 위해 다음 메시지가 표시됩니다.

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Varnish 서버에 로그인하고 다음 명령을 입력합니다.

```shell
netstat -tulpn
```

특히 다음 출력을 찾습니다.

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

위의 예는 80번 포트에서 실행되는 Varnish와 8080번 포트에서 실행되는 nginx를 보여줍니다.

`varnishd`에 대한 출력이 표시되지 않으면 Vannish가 실행 중인지 확인하십시오.

[`netstat`개 옵션](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html)을 참조하세요.

## Commerce 소프트웨어 설치

아직 설치하지 않았다면 Commerce 소프트웨어를 설치합니다. 기본 URL을 입력하라는 메시지가 표시되면 Varnish는 모든 수신 HTTP 요청을 수신하므로 Varnish 호스트와 포트 80(Varnish용)을 사용합니다.

Commerce 설치 시 발생할 수 있는 오류:

```text
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

```shell
varnishlog
```

웹 브라우저에서 임의의 Commerce 페이지로 이동합니다.

명령 프롬프트 창에 긴 응답 헤더 목록이 표시됩니다. 다음과 같은 헤더를 찾습니다.

```text
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

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

For example,

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

다음과 같은 헤더를 찾습니다.

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
