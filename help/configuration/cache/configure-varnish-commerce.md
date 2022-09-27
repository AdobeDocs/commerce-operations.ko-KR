---
title: 상거래에 대한 변형 구성
description: Commerce 응용 프로그램의 Varnish 구성 파일을 업데이트하고 관리하는 방법을 알아봅니다.
source-git-commit: d451ea025a6f4fc8a4a9f15ca83896a63058a3a0
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Varnish를 사용하도록 상거래 응용 프로그램 구성

Varnish를 사용하도록 상거래를 구성하려면 다음을 수행하십시오.

1. 관리자로 관리자에게 로그인합니다.
1. 클릭 **[!UICONTROL Stores]** > 설정 > **구성** > **고급** > **시스템** > **전체 페이지 캐시**.
1. 에서 **[!UICONTROL Caching Application]** 목록, **바니쉬 캐싱**.
1. 에 값을 입력합니다. **[!UICONTROL TTL for public content]** 필드.
1. 확장 **[!UICONTROL Varnish Configuration]** 다음 정보를 입력합니다.

   | 필드 | 설명 |
   | ----- | ----------- |
   | 액세스 목록 | 정규화된 호스트 이름, IP 주소 또는 [클래스 없는 도메인 간 라우팅(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 컨텐츠를 무효화할 IP 주소 범위입니다. 자세한 내용은 [Varnish 캐시 제거](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | 백엔드 호스트 | Varnish의 정규화된 호스트 이름 또는 IP 주소를 입력하고 수신 포트를 입력하십시오. _백엔드_ 또는 _원본 서버_; 즉, Varnish가 가속화하는 컨텐츠를 제공하는 서버입니다. 일반적으로 웹 서버입니다. 자세한 내용은 [Varnish 캐시 백엔드 서버](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | 백엔드 포트 | 원본 서버의 수신 포트입니다. |
   | 유예 기간 | 유예 기간은 백엔드가 응답하지 않는 경우 Varnish가 오래된 컨텐츠를 제공하는 기간을 결정합니다. 기본값은 300초입니다. |

1. 클릭 **구성 저장**.

C 명령줄 인터페이스 도구를 사용하여 Admin에 로그인하는 대신 명령줄에서 Varnish를 활성화할 수도 있습니다.

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Varnish 구성 파일 내보내기

관리자에서 Varnish 구성 파일을 내보내려면 다음을 수행합니다.

1. 내보내기 단추 중 하나를 클릭하여 `varnish.vcl` 바니쉬와 함께 사용할 수 있습니다

   예를 들어 Varnish 4가 있는 경우 **Varnish 4용 VCL 내보내기**

   다음 그림은 예를 보여줍니다.

   ![관리자에서 Varnish를 사용하도록 상거래 구성](../../assets/configuration/varnish-admin-22.png)

1. 기존 백업 `default.vcl`. 그런 다음 이름을 변경합니다 `varnish.vcl` 방금 내보낸 파일 `default.vcl`. 그런 다음 파일을 `/etc/varnish/` 디렉토리.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe을 여는 것이 좋습니다. `default.vcl` 값을 변경하고 `acl purge` Varnish 호스트의 IP 주소로 이동합니다. (여러 호스트를 별도의 줄에 지정하거나 CIDR 표기법을 사용할 수도 있습니다.)

   For example,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 가변 상태 검사 또는 유예 모드 또는 saint 모드 구성을 사용자 정의하려면 다음을 참조하십시오 [고급 변명 구성](config-varnish-advanced.md).

1. Varnish 및 웹 서버를 다시 시작합니다.

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 정적 파일 캐시

정적 파일은 기본적으로 캐시되지 않지만 캐시하려면 섹션을 편집할 수 있습니다 `Static files caching` VCL에서 다음 컨텐츠가 있어야 합니다.

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Varnish를 사용하도록 Commerce를 구성하기 전에 이러한 변경 작업을 수행해야 합니다.
