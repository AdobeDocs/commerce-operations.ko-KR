---
title: Commerce에 대한 바니시 구성
description: Adobe Commerce 애플리케이션에 특별히 Varnish를 구성하는 방법에 대해 알아봅니다. 구성 파일 업데이트 및 관리 기술을 살펴봅니다.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Vannish를 사용하도록 Commerce 애플리케이션 구성

Vanish를 사용하도록 Commerce을 구성하려면 다음을 수행하십시오.

1. 관리자로 관리자에 로그인합니다.
1. **[!UICONTROL Stores]** > 설정 > **구성** > **고급** > **시스템** > **전체 페이지 캐시**&#x200B;를 클릭합니다.
1. **[!UICONTROL Caching Application]** 목록에서 **바니시 캐싱**&#x200B;을 클릭합니다.
1. **[!UICONTROL TTL for public content]** 필드에 값을 입력하십시오.
1. **[!UICONTROL Varnish Configuration]**&#x200B;을(를) 확장하고 다음 정보를 입력하십시오.

   | 필드 | 설명 |
   | ----- | ----------- |
   | 액세스 목록 | 콘텐츠를 무효화할 정규화된 호스트 이름, IP 주소 또는 [CIDR(Classless Inter-Domain Routing)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 표기법 IP 주소 범위를 입력하십시오. [바니시 캐시 제거](https://varnish-cache.org/docs/3.0/tutorial/purging.html)를 참조하십시오. |
   | 백엔드 호스트 | Varnish _백엔드_ 또는 _원본 서버_&#x200B;의 정규화된 호스트 이름 또는 IP 주소 및 수신 포트를 입력하십시오. 즉, Varnish 콘텐츠를 제공하는 서버는 속도가 빨라집니다. 일반적으로 웹 서버입니다. [Varnish 캐시 백 엔드 서버](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)를 참조하십시오. |
   | 백엔드 포트 | 원본 서버의 수신 포트입니다. |
   | 유예 기간 | 백엔드가 응답하지 않는 경우 Vannish가 오래된 콘텐츠를 제공하는 기간을 결정합니다. 기본값은 300초입니다. |
   | 매개변수 크기 처리 | 전체 페이지 캐싱을 위해 [&#x200B; HTTP 끝점에서 처리할 최대 &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles)레이아웃 핸들[`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) 수를 지정합니다. 크기를 제한하면 보안과 성능을 향상시킬 수 있습니다. 기본값은 100입니다. |

1. **구성 저장**&#x200B;을 클릭합니다.

C 명령줄 인터페이스 도구를 사용하여 Admin에 로그인하지 않고 명령줄에서 Varnish를 활성화할 수도 있습니다.

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Vannish 구성 파일 내보내기

관리자에서 Vannish 구성 파일을 내보내려면 다음을 수행합니다.

1. 내보내기 단추 중 하나를 클릭하여 Vannish에 사용할 수 있는 `varnish.vcl`을(를) 만듭니다.

   예를 들어, Varnish 4가 있으면 **Varnish 4에 대한 VCL 내보내기**&#x200B;를 클릭합니다

   다음 그림은 예를 보여 줍니다.

   ![관리자에서 바니시를 사용하도록 Commerce 구성](../../assets/configuration/varnish-admin-22.png)

1. 기존 `default.vcl` 백업. 그런 다음 방금 `varnish.vcl`(으)로 내보낸 `default.vcl` 파일의 이름을 바꿉니다. 그런 다음 파일을 `/etc/varnish/` 디렉터리에 복사합니다.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe에서는 `default.vcl`을(를) 열고 `acl purge`의 값을 Varnish 호스트의 IP 주소로 변경할 것을 권장합니다. (여러 호스트를 별도의 줄에 지정하거나 CIDR 표기법을 사용할 수도 있습니다.)

   For example,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Vagrant 상태 검사 또는 유예 모드 또는 saint 모드 구성을 사용자 지정하려면 [고급 바니시 구성](config-varnish-advanced.md)을 참조하십시오.

1. Vannish와 웹 서버를 다시 시작합니다.

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 정적 파일 캐시

정적 파일은 기본적으로 캐시되지 않아야 하지만 캐시하려면 VCL에서 `Static files caching` 섹션을 편집하여 다음 내용을 포함할 수 있습니다.

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Vanish를 사용하도록 Commerce을 구성하기 전에 이러한 변경 작업을 수행해야 합니다.
